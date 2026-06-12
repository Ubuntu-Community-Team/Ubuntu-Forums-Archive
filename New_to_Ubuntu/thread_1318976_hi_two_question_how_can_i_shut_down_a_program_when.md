---
title: "hi two question how can i shut down a program when its craashed and im traped in it"
date: 2009-11-08
forum: New to Ubuntu
---

### Post by blake7 on 2009-11-08
yea i was playing warzone and when i went to quit it did not shut down properly but got traped in the last stage

also with wesnoth

can you help thank you

---

### Post by kyuubi777 on 2009-11-08
run app system monitor.. go to the processes tab and find the one that is causing the trouble, and end it... theres also a widget under gnome to do this.. you can find it by right clicking the pannel and clicking +add to panel.. forgot what its called though

---

### Post by blake7 on 2009-11-08
sorry but how can i do that if im still trapped inside the program

thank you

---

### Post by kyuubi777 on 2009-11-08
oh, do you mean it runs full screen?.... can you still switch desktops when it freezes up? because if you can then you can access the system monitor or the widget.

---

### Post by blake7 on 2009-11-08
no really it just freezes and their is nothing i can do apart from pull the plug

is thier not a key combo that i can do so it make system monitor pops up 


cheers

---

### Post by to3000 on 2009-11-08
you should add "force quit" to your panel.

to do this:

[LIST]
[*]right click on a empty piece of the panel
[*]click add to panel
[*]find "force quit"
[*]click add
[/LIST]

when the program crashes click the icon and then click the window a screen will come up saying something and press force quit to close the program.

---

### Post by kyuubi777 on 2009-11-08
> **to3000 said:**
> you should add "force quit" to your panel.
yeah, but i think his issue is that the prog. runs full- screen and apparently can't access any of his other desktops.. idk about this one.. i'm sure there is a way.. i'd actually like to know this myself

---

### Post by pmooney78 on 2009-11-08
Here's a couple of things to try ...

Type Alt+F2. That should bring up the "Run Application" dialog. Type "gnome-terminal" (without the quotes). Hopefully, that will bring up a terminal, if the system isn't borked too badly. Once you've got a terminal up, you can use it to kill applications ...

Type "pidof [application-name]' (again, no quotes), where [application-name] is the actual name of the file on your hard drive that actually gets run when the application is started. For instance, the application name for Battle for Wesnoth is "wesnoth" (no quotes, lowercase ... case is important). So you'd type "pidof wesnoth" ... and the terminal will spit out the process identifier ID for the program; it'll most likely be a 4- or 5-digit number. Once you have the process number, you can type "kill [process number]" (no quotes, substitute the process ID number you got in the previous step), which will force the program to quit.

This is kind of awkward, yes? Alternately, you could just run the graphical system monitor directly ... you could do this even if your menu bar is hidden. Again, you would type Alt+F2 to bring up the "Run Application" dialog, then type "gnome-system-monitor" (I'm going to stop reminding you to remove quotes at this point ...) to bring up the graphical monitor. You would then use it to kill the offending program: Go to the "Processes" tab, find the program, right-click on it, and choose "End Process." Give it, say, ten or fifteen seconds (more if you have a very slow system), and if it doesn't end the program, right click on the process name again and choose "Kill Process." (I think this is more invasive and more likely to cause system instability.)

If you have to kill an application all the time, you might want to install the pkill program, which gives you a quicker way to kill an application. From a terminal, type "sudo apt-get install pkill", enter your password, and wait for the process to complete. Then, when you want to kill a program, you can just type Alt+F2 to get the "Run Application" dialog and type "pkill [application name]", where [application name] is the name of the program as the operating system sees it. Of course, if you don't know the formal application name, pkill won't help until you open up the system monitor ... but you can find it there, and you'll quickly learn the names of the few programs that freeze your system.

If you've installed a Windows program that you're running through Wine (you're likely to know if this is the case ... you're probably launching it by going to a menu called "Wine" under your main menu) and THAT's freezing your system, you can bring up a terminal and type "wineserver -k" ... this will kill ALL programs running under Wine. (If this whole paragraph makes absolutely no sense to you, just ignore it.)

The panel applet "Force Quit" mentioned previously is also a good option if you have programs that freeze frequently and the panel is still accessible ... maybe not so helpful if you're running in full-screen and can't see the panel.

As a second-to-last resort, you can semi-gracefully force your system to restart by opening up a terminal and typing "sudo shutdown -r now" ... you may lose unsaved changes to documents this way.

If all else fails, turn your computer off, then turn it back on. Hopefully something else is more helpful than this paragraph.

Hope that helps!

---

### Post by kyuubi777 on 2009-11-08
god, i feel soo stupid right now.. i didn't even think of Alt F2... :( and with that can't he just run System Monitor and kill processes gui style?

---

### Post by Tyke91 on 2009-11-08
press alt+sysrq+k and you will restart your x session (killing all programs (except daemons... aka crond, sshd, as well as anything started by other users))

---

### Post by vamc on 2009-11-08
If atall u can open Terminal,u can do this:type "xkill".U will get a msg saying to click on the window u want to shut.click on the required window.See if it works.

---

### Post by blake7 on 2009-11-08
that is very good thank you for all you have done,,,it would be nice thoe in the future just to have a key short cut.....
cheers


ps is any one elses haveing problems with closeiing down these programs

---

### Post by blake7 on 2009-11-08
alt+sysrq+k 


what key is sysrq?????

cheers

---

### Post by kyuubi777 on 2009-11-08
it's different for each keyboard layout.. mine's actually a subkey Fn + delete = SysRq

---

### Post by Tyke91 on 2009-11-08
> **blake7 said:**
> alt+sysrq+k 


what key is sysrq?????

cheers
like kyuubi said, it's different on all keyboards.

Mine is right below the print screen button.

ALTERNATELY: [https://wiki.ubuntu.com/X/Config/DontZap](https://wiki.ubuntu.com/X/Config/DontZap)

---

### Post by Paqman on 2009-11-08
Alt-F2 > xkill > click on misbehaving app. Job Done.

---

