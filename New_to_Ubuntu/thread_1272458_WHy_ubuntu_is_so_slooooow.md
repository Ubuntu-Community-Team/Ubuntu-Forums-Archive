---
title: "WHy ubuntu is so slooooow??"
date: 2009-09-22
forum: New to Ubuntu
---

### Post by MedeX on 2009-09-22
Iam using ubuntu 9.04 ( jaunty ) I have 640 mb ram... P4 2.7Ghz processor.. Intel i915 motherboard... I am not using 95% of the compiz extra effexcts....... why the hell it is so slooooooow??   Firefox lags.. i even cant drag a open window smoothly... jerks jerks jerks is it meant to be like this?? Gezz Even vista runs faster thn this on my p.c ermmmm pls tell me whts the bug otherwise i am goin to bump it tonite....

---

### Post by scragar on 2009-09-22
Would you mind keeping top open and letting us know what's using the most CPU power at times?
You might also want to check ram usage```
free -m
```I would be interested to know the results.

---

### Post by halitech on 2009-09-22
what video card do you have? have you installed the restricted drivers for it (if they exist)?

LSPCI will list your video card if you don't know offhand.

---

### Post by farsight on 2009-09-22
If you have just installed Ubuntu 9.04, have you checked update manager? I know the moment I used update manager post-installation a huge list of possible updates were presented to me.

Also, are you running ubuntu through Wubi or as standalone operating system? If it is the foremost then you may wish to try the latter for increased performance.

You may also have enabled the top end desktop effects, which with an older video card would result in less than optimal effects (see halitech's post).

Keep us posted,
Farsight

---

### Post by automaton26 on 2009-09-22
Have you installed it onto the hard drive, or are you just booting from a LiveCD or LiveUSB ?

Did you create a swap partition that was at least the same size as your RAM ?

---

### Post by MedeX on 2009-09-22
Graphic card is Intel 915Gl/GV ( 3D graphic card 128 mb video memory ) and and and and.. I said 95 % of the compiz extras are still disabled no cube.. no animation nothng... It is installed on second partition ( 40 GB ) .. am using xp on other partition.... I dont knw about restricted drivers coz a geek of this forum said that the drivers are already installed... :confused:   Huh plz guide me if i need to dwonload or install its video drivers......




[IMG]http://i38.tinypic.com/2mwd41.png[/IMG]

---

### Post by philinux on 2009-09-22
Close all your running apps like firefox etc. and open a terminal. App>accessories>terminal and use the command 

```
top
```

See whats using cpu resources.

---

### Post by 3rdalbum on 2009-09-22
Run the "top" command and tell us what stays near the top of the list. This is your CPU-muching culprit.

My intuition is that it's that composited sidebar thingy you're running, but it pays to make sure.

---

### Post by Bölvaður on 2009-09-22
[3rdalbum]("http://ubuntuforums.org/member.php?u=61044") are you sure there are drivers for his graphic card? Just hearing the word *Intel* when using Jaunty is enough to make me shiver.

Try disable all visual effects, no compiz at all.
Didn't work?

Well then some program is hogging the CPU or your Intel graphic card doesn't have the proper driver installed.

To know if there is some program hogging the CPU use the top command like suggested, as it gives you pretty accurate idea on who is using the cpu and how much.

To know if you need a new driver or kernel please enter this command ```
lspci | grep VGA
``` and hope you will not see something like* Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)*
it might be worth it to also post the results from ```
glxinfo | grep client
``` and for a quick unreliable fps test ```
glxgears
``` and close it with ctrl+c or by closing the window when it has run for half a minute.
If it is the graphic card that is faulty, then you already know the thread Im going to suggest you to check out. [http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582) follow everything written for **Optimal**. And then you will have to boot up the new kernel you installed from GRUB (you probably cannot go with the default as if you do you will not be harvesting the reaps from what you did)

---

### Post by HarrisonNapper on 2009-09-22
System>Administration>Restricted Drivers should give you the option to select a video driver to make sure you're using the most recent restricted driver for your GPU.

---

### Post by c0mput3r_n3rD on 2009-09-22
Don't just ditch Ubuntu, there's a fixable problem here.  Ubuntu is wayyy less resource intensive than winblows, especially if vista is running faster!  I put ubuntu on all of my old laptops/desktops because the performance is almost doubled.

---

### Post by Sir Jasper on 2009-09-22
Hi,

You can use top or htop but if you go to the Processes section of the System Monitor (shewn in your picture) that is very easy to read (athough it itself seems to use significantly greater resources than either top or htop so I suggest you do not leave it running).

If you click on the column heading of CPU or Memory, as I expect you already know, you can sort usage from high to low. Edit the frequency to say, 3 seconds if that makes viewing easier on the eyes.

My regards

---

### Post by MedeX on 2009-09-22
```
wrath@Wrath:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller
wrath@Wrath:~$ glxinfo | grep client
get fences failed: -1
param: 6, val: 0
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GL_3DFX_texture_compression_FXT1, GL_APPLE_client_storage, 
wrath@Wrath:~$ glxgears
get fences failed: -1
param: 6, val: 0
2274 frames in 5.0 seconds = 454.460 FPS
2700 frames in 5.0 seconds = 539.863 FPS
2683 frames in 5.0 seconds = 535.844 FPS
2312 frames in 5.0 seconds = 462.297 FPS
2609 frames in 5.0 seconds = 521.751 FPS
2810 frames in 5.0 seconds = 561.981 FPS
2804 frames in 5.0 seconds = 560.642 FPS
2519 frames in 5.1 seconds = 492.624 FPS
2833 frames in 5.0 seconds = 564.648 FPS
2812 frames in 5.0 seconds = 562.399 FPS
2831 frames in 5.0 seconds = 566.151 FPS
2804 frames in 5.0 seconds = 560.632 FPS
2814 frames in 5.0 seconds = 562.769 FPS
2820 frames in 5.0 seconds = 563.849 FPS
2812 frames in 5.0 seconds = 562.279 FPS
2816 frames in 5.0 seconds = 563.135 FPS
2687 frames in 5.0 seconds = 537.395 FPS
2527 frames in 5.0 seconds = 505.309 FPS
2808 frames in 5.0 seconds = 561.561 FPS
2667 frames in 5.0 seconds = 532.956 FPS
2805 frames in 5.0 seconds = 560.867 FPS
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
      after 174106 requests (174018 known processed) with 0 events remaining.
wrath@Wrath:~$ 
```

I just restarted my sys and shooted that TOP command and that sidebar thingy is not working now... -->>



```
wrath@Wrath:~$ top

top - 20:34:47 up 1 min,  2 users,  load average: 1.40, 0.45, 0.16
Tasks: 113 total,   2 running, 111 sleeping,   0 stopped,   0 zombie
Cpu(s):  6.6%us,  4.0%sy,  0.0%ni, 85.4%id,  3.6%wa,  0.3%hi,  0.0%si,  0.0%st
Mem:    629540k total,   295384k used,   334156k free,    23684k buffers
Swap:  1662688k total,        0k used,  1662688k free,   132936k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 2452 root      20   0  320m  19m 9424 S  3.7  3.2   0:02.01 Xorg               
 3017 wrath     20   0 32132  13m 9284 R  3.3  2.3   0:00.51 gnome-terminal     
 3036 wrath     20   0  2448 1172  912 R  0.7  0.2   0:00.03 top                
    1 root      20   0  3084 1888  564 S  0.0  0.3   0:01.21 init               
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S  0.0  0.0   0:00.02 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0         
    6 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 events/0           
    7 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khelper            
    8 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 kstop/0            
    9 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kintegrityd/0      
   10 root      15  -5     0    0    0 S  0.0  0.0   0:00.01 kblockd/0          
   11 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid             
   12 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify       
   13 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 cqueue             
   14 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ata/0              


```


P.s!! Fellas am noob regarding linux at the moment i even dont knw whats jautny and hardy and which version i need to use... huh and
[B]
System>Administration>Restricted Drivers  [/B]THers no restricted drivers tab here :confused: and in the HARDWARE DRIVERS section it says there are no proprietary drivers in used on this system... grr

---

### Post by Daylon on 2009-09-22
If your video card does not show up in hardware drivers simply go to your Desktop right click and hit Change Desktop Background go ahead to the last tab and select Extra, then go back to Hardware Drivers and it will show you your video card and select the lastest version. It might seem like a too simple answer but that's what worked for me I hope it is that easy for you! Also do NOT ditch ubuntu because of that small problem, in Ubuntu anything can be fixed to your liking! I have learned this in a small amound of time I've only been using Ubuntu for 2 weeks max. Best of luck and give us some feedback. Take care.

---

### Post by achase79 on 2009-09-22
Also if you want to boost performance you may want to look into a lighter desktop manager instead of gnome.  There are several options: XFCE, LXCE, OpenBox, etc.  These make my older system run great and even have some options I like better.

---

### Post by Bölvaður on 2009-09-22
[SIZE=4]**MedeX** _read this before_ you read the ones above me[/SIZE] *and the post below me*
What the others suggested will not work, as it is the same thing as you have already tried (nothing showed up under Hardware Drivers)

Jaunty = Ubuntu 9.04 Jaunty Jackalope
Ibex   = Ubuntu 8.10 Intrepid Ibex
Hardy  = Ubuntu 8.04 Hardy Heron
Where the number is the year and month it was released.

if you dont know which version you got then use this command```
lsb_release -a
```Jaunty is a release when the intel graphic card failed. But dont worry even if you got that version (read below)



Findings:

According to the output of the commands I dont see anything out of the ordinary. The graphical card isn't powerful but it is way more powerful than the one I got in my laptop.

Also there is no process hogging the CPU (might that be because that side bar wasn't running while you did that)

Conclusion:
There is nothing wrong at the moment you ran top, but there might be a program that wasn't running at that time which is causing you this screenlag.
The graphic card does have a working driver... and even if it wasn't the correct one it seems to be doing well enough (difficult to say if  you should run compiz at all or not, something you will have to figure out your self)



Next step is to have top running in the background and try to notice which process begins to hog the cpu when you have screenlag.
Also try to close those programs (like xkill command where you enter the command into terminal and click the window of the program you want to kill)

---

### Post by halitech on 2009-09-22
Here is some info on getting an Intel video card working better if you are using Jaunty (9.04)

[http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)

---

### Post by MedeX on 2009-09-22
[LEFT]**@ [Bölvaður  ]("http://ubuntuforums.org/member.php?u=338535")**[COLOR=Black]Thanx a lot.. you cleared everything to me.... i dint know that i am using the version which is in a way not meant to be used with Intels graphic card... Ya u said that rite it seems to work tho...  Well talkin bout COmpiz i just updated this version Jaunty 9.04... and what i discovered is COmpiz setting manager is gone that means tht its obvious now i am not supposd to lame my time on it...  


Tho its workin okay now... ( and the lag thing ... ummm i can add it to an exception coz after knowing the whole thing am satisfied with it )....  **Plz tell me whether i shud go back to the previous release??** ... Just to the time i upgrade my p.c with the best compatible hardware available.... [/COLOR][COLOR=Black]Coz i really wana use Linux frm now on[/COLOR][COLOR=Black] 

P.s!! At all who replied am thankful to you... 


@ Sir Jasper.. Your reply was really something tht made my day... it showed concern hehehe.. thank yew!!
[/COLOR][/LEFT]

---

### Post by QIII on 2009-09-22
You can find some help with work-arounds to the Intel graphics issue here (read down a ways).

[http://www.ubuntu.com/getubuntu/releasenotes/904](http://www.ubuntu.com/getubuntu/releasenotes/904)

You can get away from the Intel graphics problem altogether by installing Intrepid, but try to get the Intel business sorted out in Jaunty first.

I haven't been able to test the promised improvements vis-a-vis Intel graphics in Karmic, because none of my machines use Intel chipsets.

When Karmic comes out, I hope they really have dealt with this.

---

### Post by CaptainMark on 2009-09-22
Another one converted, welcome to linux, sit down, enjoy yourself and do whatever the hell you like because thats more than you could ever do with windows.

---

