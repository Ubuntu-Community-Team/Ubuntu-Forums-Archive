---
title: "help! screen display crashing on startup"
date: 2010-01-03
forum: New to Ubuntu
---

### Post by Devlove on 2010-01-03
Dear forum,

I am absolutely new to linux, and am using Ubuntu 9.04. Since loading it a month ago, I have had periodic problems on start-up i.e. it shows that Ubuntu is loading, but then, before I get to the login/password prompts, the screen goes blank. I figured it was to do with graphics drivers, so loaded what I thought would help - namely ATI hardware accelarator. However, now, I cannot get to the login screen at all. It shows Ubunu is loading, but then, the screen flickers insanely, the ubuntu logo rolls down the screen and lastly, the system hangs, with a band of solid colour just sitting across the screen.
I am using a Packard Bell Easy Note laptop.
Please help! All my work is on that machine.
Thanks very much

---

### Post by Methuselah on 2010-01-03
When it hangs and shows the band of solid color can you hit CRTL+ALT+F2 (ie press them all at once) and does it show a black screen with some text asking for a login?

---

### Post by Devlove on 2010-01-03
Hi - I tried hitting CTRL-ALT-F2 when it hangs. It is not doing anything. Just remains hanged, not even showing a prompt.

---

### Post by Methuselah on 2010-01-03
OK.

Restart ubuntu and watch out for the GRUB menu.
If you are not dual booting you may not get a menu by default.
In that case just keep pressing ESC key before Ubuntu loading screen comes up.
In the list that you'll see choose the option with the same numbering as the one on top but with 'recovery' beside it.
Let it boot then choose the option to repair broken packages at the menu that appears and let it reboot normally when it is done.

Post back.
I have another idea if this does not work out.

---

### Post by Devlove on 2010-01-03
hi. I tried that. Again, it hangs, but now shows great swathe of green and white across most of the screen! basically, a frozen flicker.

I have typed out below the gist of the readout I got after doing 'repair broken packages' and prior to 'resume normal boot'

   Failed to fetch : archive 

/ security 

/ archive canonical
   
  Some index files failed to download...
   
  May want to run apt-get update...
   
  Building dependency tree...
  Reading state info...
  O upgraded 0 newly installed 0 to remove 0 not upgraded
  Reading package lists...
  Building dependency tree...
  Reading state info...
  Calculate upgrade &#8211; done
  0 upgraded 0 newly installed 0 to remove, and 0 not upgraded
  
any thoughts? very much appreciate your help.

---

### Post by Methuselah on 2010-01-03
OK, fine.

Do what I told you before to get the menu and select the 'recover' option.
Scroll down to the bottom this time and choose to drop to a 'root shell'.

Execute
 
```

dpkg-reconfigure xserver-xorg

```

Then

```

reboot

```

Try to reboot normally.

---

### Post by Devlove on 2010-01-03
I did that. However, after executing 'dpkg-' I was taken through a number of screens asking how I should configure my video and keyboard settings. I left them as they were or followed the guidance given e.g. choosing pc104 for a european style keyboard. I tried to circumvent this but had to go through it.

i then executed reboot - but alas, it still misbehaves and takes me to a hanged screen: flicker of band of colour, then, flickers across the scree, and then a frozen band of colours towards top of screen

I rebooted and tried the whole thing again - no luck, same hanged result

---

### Post by Methuselah on 2010-01-03
If you can get back to the root shell do

aticonfig --initial

Reboot normally.

I'm really hoping this gets fixed for you.
I had one bad experience with ATIs proprietary driver and have avoided it ever since.

---

### Post by Devlove on 2010-01-03
Ok... I did 'aticonfig --initial' and the response I got was:
    
  'No supported adapters detected'


I also made the backup and other changes as you suggested, which were accepted, but still, I see the same scree/hanged


Sorry - I don't know what's going on. apologies also for my slowness. I am in Kampala and internet is a bit tricky.

---

### Post by Methuselah on 2010-01-03
It does not seem as if you have the proprietary driver.

Here is what I am going to suggest next.

Get back to the root shell.

Execute

```

X -configure

```
It should claim to have generated a file at /root/xorg.conf.new

Then let us back up your existing file in case the generated one is worse
```

mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak

```

Then copy the generated one to the location of the original
```

cp /root/xorg.conf.new /etc/X11/xorg.conf

```

Try to reboot normally
*crosses fingers*

---

### Post by Devlove on 2010-01-03
when you say 'reboot normally' do you mean I code 'reboot' and hit enter?

---

### Post by Devlove on 2010-01-03
ok - have rebooted - and ubuntu is no running a routine check of drives. Still not come to login window yet

---

### Post by Methuselah on 2010-01-03
Yes, that's what I meant Devlove...to enter 'reboot' and let it start without hitting ESC and going into recovery.

---

### Post by Devlove on 2010-01-03
hi Methuselah, I did that. ubuntu ran a routine check of drives and found no problems; but again, its hanged, as before. Aargh!

---

### Post by Methuselah on 2010-01-03
Wow, I am basically out of ideas.
If you can get back to the root shell (reboot, esc, root shell)
Do
```

tail /var/log/Xorg.0.log

```

Do you see any errors...at least that could give some ideas of what is wrong.

As a last resort, if you have the installation CD you should still be able to boot from it.
So you can use that to boot and rescue your data to an external drive then reinstall if necessary.

---

### Post by Devlove on 2010-01-03
Hi again, I did that, and I am typing below the output:

(II) Initializing built-in extension 
SYNC 
XKEYBOARD
XC-MISC
SECURITY
XINERAMA
XFIXES
RENDER
RANDR
COMPOSITE
DAMAGE

does that offer any clues? else I will try and get hold of the installation CD tomorrow

---

### Post by Methuselah on 2010-01-03
Seems as if it is not even finishing initialization.
It really is just hanging as it starts up.
It could be that the DAMAGE extension is causing problems and if it could be disbaled Xorg might start.
I really don't know at this point though.

---

### Post by Devlove on 2010-01-03
Ok. thank you very much for all the help. I will attempt to start-up using installation CD tomorrow. But thank you so much for taking the time with this. Meanwhile, if you know anything else I should try, please let me know.

---

### Post by Devlove on 2010-01-05
Hi again Methuselah, following on from the discussion above... just to say I have reloaded Ubuntu 9.04. Now, I noticed that things were fine until I did the recommended system update. I now find I'm having the same problem as before: sometimes, the screen goes blank after I start-up but before I can log-in. This also happens when emerging from suspend/hibernate stage or when restarting. However, at other times, things are just fine.
Reading the Ubuntu help pages I find this could be because of my video driver; which is:

01:05:0 VGA compatible controller: ATI technologies Inc RC410 [Radeon Xpress 200M]

Does this offer you any clues as to what is wrong an what I need to do? I tried to find how I could add the appropriate driver, but must confess, got pretty lost. 

Your guidance here much appreciated.

---

### Post by Methuselah on 2010-01-05
Hi Devlove, 

Sometime after this thread I discovered another thread full of people experiencing the same problem after running an update.

[http://ubuntuforums.org/showthread.php?t=1305459](http://ubuntuforums.org/showthread.php?t=1305459)

It seems there is a bug related to the restricted ATI drivers and a kernel update that is causing this problem.

Did you enable the restricted driver this time as well?

---

### Post by Devlove on 2010-01-06
Hi - No, i didn't enable any restricted drivers. All I did was reinstall 9.04. Then, I did the recommended upgraded, which I think means I'm now running 9.1 

I tested the on/off sequence several times with 9.04 and it started ok. However, no sooner had all the upgrades been effected and I restarted, that the screen went blank before login and hanged. 

unless the restricted driver is part of the recommended update, it would not have been installed.

This morning I started in recovery mode, repaired broken packages and my laptop is now running fine; just don't know if it will run the next time.

---

### Post by Devlove on 2010-01-06
When I searched for propriety hardware under System/ - it said it couldn't find any. That's werid because I do have ATI 200M; which should mean I need to enable it. Unfortunately, I've just not been able to figure out how to run the scripts to do this. Ubuntu Help recognises ATI creates display problems in monitor and suggests changes to the AGPmode - but again how do I actually make these changes? I was afraid to experiment in case I screw up things even worse. Would be grateful for your advice.

---

### Post by Methuselah on 2010-01-06
Do you remember how to get to a command line prompr as I told you earlier in the thread?

Do

```

cat /etc/X11/xorg.conf | grep Driver

```

and tell me what it says.
I am not particularly interested in the lines with "kbd" and "mouse" but the other is important.
I have seen people fix this issue by reinstalling xorg.
That's what I am going to let you do but I want to know if it is trying to use fglrx driver.

---

### Post by Devlove on 2010-01-06
Hi - I did that. It does not return any information! Just brings me back to the command line prompt. I tried both by rebooting and dropping to shell and inputting the code; and later, after log-on, opened a terminal and tried again. In both cases, no information returned. Just goes back to command line prompt. Am I doing something wrong here?

---

