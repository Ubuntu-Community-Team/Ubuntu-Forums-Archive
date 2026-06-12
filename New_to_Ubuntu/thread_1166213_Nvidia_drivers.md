---
title: "Nvidia drivers"
date: 2009-05-21
forum: New to Ubuntu
---

### Post by djen9999 on 2009-05-21
I just did a clean install of Jaunty and when I installed the recommended driver for my Nvidia card(180), all I got was a black screen with a thin white line at the top When I rebooted, .  I'm in recovery mode now and can only get screen resolution of 640 x 480 and no 3D or 2D acceleration.  This also happened when I updated to Intrepid, from Hardy but I thought it was my error.  Any ideas besides going back to Hardy?

---

### Post by KhaaL on 2009-05-21
Did you see if your videocard is supported by the driver? maybe it needs the legacy nvidia driver instead. just a thought

---

### Post by djen9999 on 2009-05-21
When I click on the Drivers section, I'm given an option of three different drivers.  The 180 driver is the recommended driver.  The 173 and the 96 are also available.

---

### Post by fillintheblanks on 2009-05-21
maybe install the driver from [http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

---

### Post by Gen2ly on 2009-05-21
What's your video-card djen9999?

---

### Post by djen9999 on 2009-05-21
The video card is GeForce 6100.

---

### Post by Gen2ly on 2009-05-21
Hmm, the normal nvidia drivers include support for that graphics card.  Maybe you should try as fillintheblanks suggested and download them manually, it's possible that the legacy drivers were installed.

---

### Post by xavierp94 on 2009-05-21
> **Dirk.R.Gently said:**
> Hmm, the normal nvidia drivers include support for that graphics card.  Maybe you should try as fillintheblanks suggested and download them manually, it's possible that the legacy drivers were installed.
When you installed it did you enable the desktop effects before restarting? I once installed the recommended driver and I set my desktop effects to high so I kept receiving a error message like that.

---

### Post by djen9999 on 2009-05-21
This is bizarre.  When I type in sh NVIDIA-Linux-x86_64-180.51-pkg2.run (or pkg1.run, I tried both)  I get an error that it can't open them.

I think I'll live with low graphics mode.

---

### Post by djen9999 on 2009-05-22
> **xavierp94 said:**
> When you installed it did you enable the desktop effects before restarting? I once installed the recommended driver and I set my desktop effects to high so I kept receiving a error message like that.

When I upgraded from Hardy to Intrepid, desktop effects were already on, so that "could" have been a problem.  This was a clean install so the first thing I did was install the "proper" driver, then restarted.

I'm seriously considering going back to Hardy, I at least had desktop effects and 3D.

---

### Post by Dave W. on 2009-05-22
Hello,

I'm a Noob and I think that I'm having the same problem.  I went to the Nvidia site and downloaded  NVIDIA-Linux-x86-185.18.04-pkg1. This one supports 6100.  I think that this is a new driver.  I really don't understand yet how to install it.  Right now I am using a legacy driver.  

If any one can tell me how to install, this may help us both.  

Thank you in advance.

Dave

---

### Post by kpkeerthi on 2009-05-22
1. Enable the recommended driver from System -> Admin -> Hardware Drivers
2. Run this command in a termina
```

sudo nvidia-xconfig

```
3. Reboot.

And post back what happened.

---

### Post by Dave W. on 2009-05-22
Well,  I'm not really sure what happened. The terminal read something about a new X configuration file being written.  I tried opening a loading the new driver and got an error in gedit.  Something about opening a binary file.

Thanks, 

Dave

---

### Post by t.rei on 2009-05-22
Do this:

Download driver from nvidia.
Logout of gnome.
Press Strg + Alt + F1 to get to a text based login.
login.
Enter: sudo /etc/init.d/gdm stop
(it will ask for your password)
cd YourDownloadLocation
sudo sh ./NVIDIA-Linux-x86-xxx.yy-pkg1.run
(xxx.yy - the version of your driver - i.e. 180.40)
follow instructions on screen, accepting the licence agreement, do not get confused that the driver sais something about not being able to download something.
reboot once sucessfull (sudo reboot)

after reboot check if the nvidia driver is used:
lsmod |grep nvidia

if not, your xorg.conf might not have been updated.

---

### Post by Dave W. on 2009-05-22
I'm sorry and embarrassed to ask this, but what is "Strg" and how to I enter it.

Thanks, Dave

---

### Post by Dave W. on 2009-05-22
Found it. " Ctrl"

Dave

---

### Post by orky7 on 2009-05-22
hi. try envy-ng it will automatically install the latest driver. u will find it in the ubuntu repository. To install the package u downloaded from the nvidia site i think u should run that package at run level 3 not at run level 5..or u can go to sysytm->admin-> hardware driver and install it and reboot(i think u have done this particular step)

anyways good luck...

---

### Post by Dave W. on 2009-05-22
Okay, let me make sure I understand this.  I've gone into synaptic and downloaded envyng-core (this is what I saw).  This has been done and this should update my driver.  It seems too easy.  I think I'm missing something.

When I check "hardware drivers" I see the same 3.  180, 173, and 96.  I have been using 96 because that has been the only one that has worked.  I'm concerned about activating 180, because if I do then I will have to do a clean install of Jaunty if my monitor doesn't work.

How do I know if I am on the right track here.

By the way thank you for your patience.

Dave

---

### Post by fillintheblanks on 2009-05-22
> **djen9999 said:**
> This is bizarre.  When I type in sh NVIDIA-Linux-x86_64-180.51-pkg2.run (or pkg1.run, I tried both)  I get an error that it can't open them.

I think I'll live with low graphics mode.



step 1 goto [http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us) and download the appropriate driver for you card. you can save it to desktop

step 2 press CTRL+ALT+F1

step 3 enter your login and password

step 4 stop the GDM by typing **sudo /etc/init.d/gdm stop**

step 5 goto where you saved the installer file by typing **cd /home/your username/Desktop**

step 6 type **sudo sh NV** press TAB it will fill out the filename for you. press enter

step 7 say N to download and Y to compile. say Y to everything else. this will install the driver

step 8 you should be back at the prompt now, type **sudo /etc/init.d/gdm REstart**

step 9 done.

---

### Post by djen9999 on 2009-05-22
Everyone has been great with their suggestions to the two Daves.  Thank you.

I don't have time right now to try the various suggestions but I will soon.

Thanks again.

---

### Post by philip.denotto on 2009-05-22
Have the same problem with a GeForce 6100 to a Lenovo L171 with Jaunty clean install.  I tried the latest instructions.  Results are still the same.  I get a blank logon in screen where I blindly type in my userid and hit enter.  Then I blindly enter my password and hit enter.  The result is a screen with just a thin white line at the top.  When I went to the NVIDIA site for the down load I selected:
Product Type:  GeForce	
Product Series: Series 6	
Operating System: Linux 32
Everything went according to the instructions, but it did not seem to work.  Any ideas on how to check on what happened?

---

### Post by Dave W. on 2009-05-22
Yes, thank you all for the great suggestions. I haven't been successful yet, but as usual,  I feel that I am learning a lot.  I hope that someday I'll be able to give  back like all of you.

    ...Time to cut the grass... before my wife gets home!!!

Dave

---

### Post by djen9999 on 2009-05-22
At least I know I'm not alone.  My stop gap measure is to log on in recovery mode get into my xorg.conf and enter my monitors resolution under Display.  When I log back on in regular mode, I get an error that the Kernal can't parse the xorg.conf but it asks if I want to work in low graphics mode.  I get a few more warning screens but I keep clicking in the affirmative and I get my desktop albeit without 3D or 2D acceleration.

I'm thinking of getting a stand alone graphics card.  One that I know is compatible.

---

### Post by oldsoundguy on 2009-05-22
I have had nothing but grief from anything above Hardy for any "effects" using either the default drivers OR going and getting the Envy package or any other method.

I use RandRotate on my main monitor to get a portrait display. Thus far, it seems the newer versions of Ubuntu disable that feature and I have NO CLUE as to how to re-enable it.  In Hardy all it took was a line of code in xorg to turn it on.

They really need to concentrate on getting both audio and video to function for most "out of the box" and forget all of the toys and seldom used programs with their constant updates.
(recent update killed my digital audio and have been unable to restore it!)

---

### Post by orky7 on 2009-05-22
@ Dave......u have only installed the envy-ng core module so u have to install the drivers via command line or install the gui of envy so that it will be easy for u to install the drivers, search in the repo u will get it.... also it is very ***_IMPORTANT_*** that u back up ur x server configuration file so that if u get stuck of something wrong happen like stuck with a blank screen u can restore the old x server config file and every thing will be restored.

so, at first if u have already installed any driver uninstall it and then install the drivers via envy-ng GUI its very easy....and don't forget to back up ur x server config file.... 

again good luck.....

---

### Post by philip.denotto on 2009-05-22
So I finally got my GeForce 6100 to work with Jaunty.  I ended up using the Nvidia 96 hardware driver.  It works fine.  I obviously don't know why the other two choices don't work, but at this time I'm just glad to get out of 600x400 mode.

---

### Post by djen9999 on 2009-05-22
Thank you Phillip.

That did the trick!

As you said, I don't know why, but it's working and that's all i care about.

Thanks!

---

### Post by Dave W. on 2009-05-22
Yes, I've been using 96 also.  


I use the hibernation feature often, but I don't think the 96 driver supports it.  

Again, I really appreciate everyone's suggestions and will keep trying them.  There is definitely a learning curve here.

Thanks everyone, 
Dave

---

### Post by djen9999 on 2009-05-22
A new wrinkle.

For the first time in a long time, I've been able to set up my desktop effects.  If I manually switch desktops using the cube, my scrolling dies.  I can't scroll up or down using the mouse or the scroll bar.

This is not a deal breaker, I'm curious if anyone else has run into this.

---

### Post by imperial99 on 2009-05-23
I installed with sh - how do you uninstall drivers?

---

### Post by Psquared on 2009-05-23
Similar problem here. I had not rebooted in awhile so I did last night. Compiz will not run. Effects will not turn on, Fusion Icon will not start, even the compiz-check script will not run. lsmod | grep nvidia shows no result, but I know I have an nvidia card in my Acer Extensa laptop.

Everything worked great before.

replace --compiz yields nothing. There seems to be no way to load compiz and nvidia. (must have been an update somewhere and I just discovered it)

Under hardware the only thing listed is the Broadcom driver. No nvidia. So Nvidia is not loading. Went to Synaptic and the same drivers are checked (180) as before.

xconfig-nvidia yields no result.

Blacklisted driver? Corrupt driver? Corrupt compiz?

Solution, unintstall everything nvidia and compiz related and then reinstall. Concerns -- may lose screen altogether.

Other options anyone?

---

### Post by djen9999 on 2009-05-23
All I have to do is resize my screen and my scrolling comes back.  Funny thing is that it doesn't happen all the time.  It's a bit of a pain but I can deal with it.  

Compiz is running beautifully for me.  Compiz icon works like a charm.  My only complaint (question) is why is the 180 driver recommended when it clearly doesn't work.  The 96 driver has been fine except for the little glitch with compiz and scrolling.

---

### Post by djen9999 on 2009-05-23
Psquared, try the 96 driver and see if that helps things.

---

### Post by Psquared on 2009-05-23
I just ran lspci and I DO NOT have the nvidia card. I am using the Intel mobile. My bad. I was thinking of my desktop.

So I had a look at /etc/X11/Xorg.conf and there is NOTHING there. Will it regenerate if I reboot or am I looking in the wrong place?

How do I regenerate an xorg.conf file while running? I am afraid if I reboot now I'll never get it back up.

Oh, and I did install the Sun version of Java recently -- could that have borked compiz? How about flash?

Thanks for your help.

---

### Post by djen9999 on 2009-05-23
You didn't back up your xorg.conf?  tsk tsk tsk:???:

Seriously - I _think_ that if you reboot and get nothing again, you can reboot into recovery mode, install the proper driver and your xorg.conf will be rewritten.  Don't take that as gospel.  Even after two years I'm still a noobie.

Compiz is still a little bizarre when it comes to running certain apps.  Running loose bindings with my nvidia card improved things tremendously.  I guess I should RFM but there are just too many things to absorb.

---

