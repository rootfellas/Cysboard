Cysboard 
=========
A lightweight system monitor similar to conky but with html and css for themes

##Usage
1. Create a theme file called main.html in ~/.config/cysboard/ (There must be a file name 'main.html').
2. Add your html code with any of the listed ids below in html tags for device info.
3. Run cysboard.

If a 'main.html' file does not exist in the config directory cysboard will start with a default theme.

##Compiling  
You must have cmake >= 3.1 and gcc >= 5.4 in order to compile

1. mkdir build
2. cmake .
3. make


##Examples
![cysboard_default](https://cloud.githubusercontent.com/assets/3809183/22162361/04db2e0c-df14-11e6-8448-45829ca36e8b.png)

Use ids like the following 

```html
<html>
<head>
    <title>Cysboard</title>
    <meta name="position_x" content="3400">
    <meta name="position_y" content="50">
    <meta name="width"  content="350">
    <meta name="height" content="350">
    <meta name="time" content="1">
    <link rel=stylesheet href="path/to/style.css" />
</head>
<body>
    <div
       <!-- os info -->
        <div .section #osinfo>
            <div >SYSTEM</div>
            <div .section-content-child>
                <p>name:   <span id="os_name"></span></p>
                <p>distro: <span id="os_distro_name"></span></p>
                <p>uptime: <span id="os_uptime"></span></p>
            </div>
        </div>
        <!-- cpu info -->
        <div id="cpuinfo">
            <div>CPU</div>
            <p>model:  <span id="cpu_name"></span></p>
            <p>vendor: <span id="cpu_vendor"></span></p>
            <p>arch:   <span id="cpu_arch"></span></p>
            <p>usage:  <span id="cpu_usage"></span> %</p>
        </div>
        <!-- mem info -->
        <div id="meminfo">
            <div>RAM</div>
            <p>free: <span id="mem_free"></span> KB</p>
            <p>used: <span id="mem_used"></span> KB</p>
        </div>
        <div>
            <p>Program 1 Output: <span id="exec_1" cmd="path/to/program"></span></p>
            <p>Program 2 Output: <span id="exec_2" cmd="path/to/program"></span></p>	    	
        </div>
    </div>
</body>
</html>
```
See sources/resources/default.html for a working theme.

##IDs
A list of currently supported information from sources. Add any of
them as an *id* attribute for a tag in your theme file.

ID             | Info
-------------- | -----------------
cpu_name       | The CPU's name                                 
cpu_usage      | The total usage of the CPU in percentages      
cpu_arch       | The CPU's architecture                         
cpu_vendor     | The CPU vendor eg. Intel, AMD                  
cpu_num_cores  | The number of physical cores                
mem_free       | The amount of free memory in KB, MB or GB                
mem_used       | The amount of used memory in KB, MB or GB                
mem_swap_total | The amount of swap memory in KB, MB or GB                
mem_total      | The total amount of physical memory available
os_name        | The name of the OS        
os_distro_name | The distribution name (*Linux only*)       
os_uptime      | The total amount of time since last boot
exec_#         | Execute a program and display its output eg. *exec_0, exec_1* etc.

Some IDs require attributes and can be used like this

	<p>Free RAM: <span id="mem_free" mul="MB"></span></p>

Atrribute       | Description                       | Applicable ID(s)
----------------| --------------------------------- | ---------------------------------------------
mul             | Display value in MB, KB or GB     | mem_free, mem_used, mem_swap_total, mem_total
cmd             | Path of program to execute        | exec_#


##Known Issues
1. Program crashes sometimes when editing themes.

##Todo
1. GPU, Disk and Network information.
2. Run commands from theme file.
