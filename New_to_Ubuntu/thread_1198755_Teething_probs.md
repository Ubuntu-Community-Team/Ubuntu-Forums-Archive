---
title: "Teething probs"
date: 2009-06-27
forum: New to Ubuntu
---

### Post by typos1 on 2009-06-27
Had ubuntu for 2 days now and going well-Thanks for all the help I ve been given. Got a couple of teething troubles though:
 
Whenever I start up ubuntu forgets my display resolution and reverts back to 800x600. Every time I change it to 1680x1050 and save settings, but its always back at 800x600 when I login. Any ideas?

and

If I disconnect the internet from the pc and re-connect it later, ubuntu wont recognise its online again it just keeps saying its offline, I have to restart for it to recognise its online again. And once it still thought it was offline when I d restarted!

---

### Post by linuxmagick on 2009-06-27
You can try setting the resolution in your xorg.conf file. In a terminal type:

sudo gedit /etc/X11/xorg.conf
Try adding a subsection like below (change the mode to whatever resolution you want), then save your changes. I had to do that on my laptop because it wouldn't remember the resolution after rebooting.


Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
[B]SubSection "Display"
Depth 24
Modes "1024x768"
EndSubSection[/B]
EndSection


I'm not really sure about your network problem.  I had some issues with the default network manager in Kubuntu so I installed wicd with sudo apt-get install wicd and it's working great.

---

### Post by -kg- on 2009-06-27
Re, your network problem:

I don't know whether you're using wireless or wired (Ethernet), but I just tried an experiment.  My laptop is using wireless, so I turned the (internal) wireless off and of course it took me off-line.  When I turned it back on, it remained off line.

I brought up the menu from the icon in the Notification Area (default, top panel to the right) and saw nothing that would enable it again, so I double left-clicked it and it reconnected and it re-established the connection.

Going to try it with my desktop (wired) now...

OK, when I disconnected my Ethernet cable it gave me the "disconnected" message, but when I plugged it back in, it automatically reconnected me without having to do it manually.  If you're connecting via Ethernet and it is doing this, then something seemingly is mis-configured (or something), being that we're both using Jaunty.

If you're using a wireless connection, now you know how to re-establish your Internet connection. Just double-(left-)click the icon.

---

### Post by typos1 on 2009-06-28
> **linuxmagick said:**
> You can try setting the resolution in your xorg.conf file. In a terminal type:

sudo gedit /etc/X11/xorg.conf
Try adding a subsection like below (change the mode to whatever resolution you want), then save your changes. I had to do that on my laptop because it wouldn't remember the resolution after rebooting.


Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
[B]SubSection "Display"
Depth 24
Modes "1024x768"
EndSubSection[/B]
EndSection


I'm not really sure about your network problem.  I had some issues with the default network manager in Kubuntu so I installed wicd with sudo apt-get install wicd and it's working great.

Tried this and it made no diference

---

### Post by swisstone198 on 2009-06-28
have you tried command

 sudo dpkg-reconfigure -phigh xserver-xorg

---

### Post by linuxmagick on 2009-06-28
If you're still having problems with the display resolution, can you post a copy of your xorg.conf so we can take a look?

---

### Post by Martje_001 on 2009-06-28
Add
```
xrandr -s 1680x1050
```
to your startup commands. It sets your resolution to 1680x1050. I don't know why it doesn't remember your settings though, it's ought to do so.

---

### Post by typos1 on 2009-06-29
> **swisstone198 said:**
> have you tried command

 sudo dpkg-reconfigure -phigh xserver-xorg
tried this and when I reboot the password screen is a much lower reolsution to what it was previously and when I ve logged in I cant change my screen res at all. It says "you do not apppear to be using your xconfig driver. Please edit yourx cofig file (just run"nvidia-xconfig" as root and restart the x server.

I typed "nvidia-xconfig" in a terminal and pressed enter and this came up:
Using X configuration file: "/etc/X11/xorg.conf".

VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
                  Device section "Configured Video Device" must have a Driver
                  line.


ERROR: Unable to write to directory '/etc/X11'.

jason@jason-desktop:~$ 

so now everything is really big and I cant reconfigure it, help!

---

### Post by typos1 on 2009-06-29
> **Martje_001 said:**
> Add
```
xrandr -s 1680x1050
```to your startup commands. It sets your resolution to 1680x1050. I don't know why it doesn't remember your settings though, it's ought to do so.
  
Sorry , but where do I find startup commands?

---

### Post by Martje_001 on 2009-06-29
This is translated, so I don't know if it's correct:

System --> Preferences --> Sessions (or Startup programs/applications)

Before you do, please do the following in a terminal:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Next, go to "Hardware driver" and re-activate your Nvidia drivers. Then reboot your system and have a look a the output of the following command:
```
xrandr
```
For example, mine looks this way:
```
Screen 0: minimum 640 x 480, current 1280 x 800, maximum 1280 x 800
default connected 1280x800+0+0 0mm x 0mm
   1280x800       60.0* 
   1024x768       60.0  
   800x600        60.0  
   640x480        60.0  

```
You can see 1280x800 is the maximum resolution I can choose. This is okay because this is my laptop ;). If you don't see 1680x1050 you haven't properly configured the Nvidia driver. Please remove everything with 'nvidia' in it from Synaptic and reinstall using jockey (i.e. Hardware Drivers).

But as soon as you see 1680x1050 you can add the command which I gave you in my previous post.

See if it works for you. If it doesn't; I'm sure we can find another way to make it happen.

Good luck!

---

### Post by typos1 on 2009-06-29
Ok I ll try it in a minute but I now have the problem with my graphics card (see above) and I need to sort that 1st...

---

### Post by Martje_001 on 2009-06-29
Try:
```
sudo apt-get remove nvidia*
```
And then restart your system and try my instructions.

You have installed the drivers using either Synaptic or 'Hardware Drivers', right?

ps: You can switch to a terminal any time using CTRL + ALT + F2 (or F3/4/5/6)

---

### Post by typos1 on 2009-06-29
Sorry, yeah, re-activated drivers and followed your advice. Still 800x600 when restart...arghh!

Think I did install using those 2 methods, not sure-I ve done so much over these last few days and its all new!

---

### Post by typos1 on 2009-06-29
Right. I m getting confused now. I uninstalled all nvidia stuf by running the command you said. Then I rebooted (was in low graphics mode). then I ran sudo dpkg-reconfigure -phigh xserver-xorg and then xrandr and got 
Screen 0: minimum 640 x 480, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 0mm x 0mm
   800x600        61.0* 
   640x480        60.0  
jason@jason-desktop:~$ 

When I go to hardware drivers in admin it says no proprietry drivers on this system. How should I re-install nvidia?

Just checked for updates got this message:W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY B152F042D246C25D
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
 
this ok?

And in start up theres just a list of apps, nowhere for me to enter anything...

---

### Post by typos1 on 2009-06-29
Help, I m in a real mess now I cant install nvidia it says it must have a driver line

---

### Post by Martje_001 on 2009-06-29
Don't panic :P

I suggest you execute these commands:
```
sudo apt-get update
sudo apt-get install medibuntu-keyring
sudo apt-get update
```
To get rid of the NO_PUBKEY error (this is a problem apart from the driver btw).

Do a
```
sudo apt-get install nvidia-96-modaliases nvidia-71-modaliases nvidia-180-modaliases nvidia-173-modaliases
```
Now you should be able to reinstall your drivers with jockey. Sorry for all the commands, it could be done through the GUI, but I would have to translate everything. Commands are much easier to give ;).

---

### Post by Martje_001 on 2009-06-29
Really, don't panic, everything is looking fine. It's just that you've got multiple problems at once ;-).

---

### Post by typos1 on 2009-06-29
> **Martje_001 said:**
> Don't panic :P

I suggest you execute these commands:
```
sudo apt-get update
sudo apt-get install medibuntu-keyring
sudo apt-get update
```To get rid of the NO_PUBKEY error (this is a problem apart from the driver btw).

Do a
```
sudo apt-get install nvidia-96-modaliases nvidia-71-modaliases nvidia-180-modaliases nvidia-173-modaliases
```Now you should be able to reinstall your drivers with jockey. Sorry for all the commands, it could be done through the GUI, but I would have to translate everything. Commands are much easier to give ;).

Right, I installed all the 180 ones as it was that type that was recommended. Didnt install the 96 and 173 ones,  I ll try that

Trying not to panic, but its hard to read the screen at this res!

---

### Post by Martje_001 on 2009-06-29
Ok, after you installed the 180-ones, how does your /etc/X11/xorg.conf look?

ps; You'll have to reboot after installing.

---

### Post by typos1 on 2009-06-29
Right, done all that but still get the message saying not using drivers. I ll try a reboot...

---

### Post by Martje_001 on 2009-06-29
Ok, and please post /etc/X11/xorg.conf here.

---

### Post by typos1 on 2009-06-29
Right. Re booted and back to normal. Normal being having to change the res evrytime I turn pc on. 

How do I find /x11/xorg.config?

---

### Post by Martje_001 on 2009-06-29
xorg.conf doens't matter, since it now works ;).

Can you post the output of
```
xrandr
```
?

---

### Post by typos1 on 2009-06-29
No, I cant. Real probs now. Had 4 firefox windows open nothing else. Started to run slow. Opened sytem monitor-was a blank white box, opened terminal, was also a blank white box. Rebooted. Same problem...And no maximaise/minimise/close controls on top right of screen anymore.

---

### Post by Martje_001 on 2009-06-29
Have you got effects enabled? Try to disable them.

ALT + F2 --> metacity --replace

Which version of Ubuntu are you using?

---

### Post by typos1 on 2009-06-29
jaunty for amd x64. When I press alt and f1 the apps menu appears

---

### Post by Martje_001 on 2009-06-29
Alt + f**[SIZE="3"]2[/SIZE]** ;)

---

### Post by typos1 on 2009-06-29
Soz, my mistake, F2 not F1 !

xrandr:
Screen 0: minimum 320 x 240, current 1680 x 1050, maximum 1680 x 1050
default connected 1680x1050+0+0 0mm x 0mm
   1680x1050      50.0     51.0    107.0* 
   1600x1024      52.0  
   1440x900       53.0  
   1400x1050      54.0     55.0     56.0  
   1360x768       57.0     58.0  
   1280x1024      59.0     60.0  
   1280x960       61.0  
   1152x864       62.0     63.0     64.0     65.0  
   1024x768       66.0     67.0     68.0  
   960x600        69.0  
   960x540        70.0  
   840x525        71.0     72.0     73.0     74.0  
   832x624        75.0  
   800x600        76.0     77.0     78.0     79.0     80.0     81.0  
   800x512        82.0  
   720x450        83.0  
   680x384        84.0     85.0  
   640x512        86.0     87.0  
   640x480        88.0     89.0     90.0     91.0  
   576x432        92.0     93.0     94.0     95.0  
   512x384        96.0     97.0     98.0  
   416x312        99.0  
   400x300       100.0    101.0    102.0    103.0  
   320x240       104.0    105.0    106.0  

This says the same as it did before!

---

### Post by typos1 on 2009-06-29
Does that asterix mean remove?

---

### Post by Martje_001 on 2009-06-29
The asterix means you're currently using that mode.

Now try adding 'xrandr -s 1680x1050' to your startup list. It will then set your resolution to 1680x1050 every time you login.

Are you still experiencing the white-screen problem?

---

### Post by typos1 on 2009-06-29
White screen prob gone. Wheres the startup list? I only have startup apps in preferences

---

### Post by Martje_001 on 2009-06-29
That should be it. Click on 'add' and give it a name (you can choose whatever you like) and in the second box:
```
xrandr -s 1680x1050
```

Edit: Test it by restarting your machine.

---

### Post by typos1 on 2009-06-29
Wahy, done! Thanks!!

Noticing the last few times I ve shut down I m getting what looks like a distorted video test card on the screen momeneterally, before it shuts down and that didnt happen before

---

### Post by Martje_001 on 2009-06-29
Pleasure ;)

Is it a big problem?

---

### Post by typos1 on 2009-06-29
Not really, doesnt look very healthy thats all. Still got no minimise/maximise/close controls at top right of windows though

---

### Post by Martje_001 on 2009-06-29
I suggest you disable effects. Right clicking on the desktop --> Change background --> Last tab --> Off / None

---

### Post by typos1 on 2009-06-29
Ok, thats sorted that. Dont know why its suddenly happend though as had it on the middle setting for 4 days with no probs.
Anyway, thank you very much for helping me sort the problem/s!

---

### Post by Martje_001 on 2009-06-29
No problem! :)

---

### Post by typos1 on 2009-06-30
Strange-the date/time/volume control/shut down controls have moved from the right to the centre, not  a problem just strange

After re-booting the trash basket has moved from the bottom right to the bottom centre, strange as well. 

Why should I get random moving of icons?

---

### Post by Garyhans on 2009-06-30
Jaunty doesn't rely so much on xorg as past releases. Although Nvidia-Settings may be in your graphics menu it won't save when ran. You should therefore do the alt f2 and run gksudo nvidia-settings set resolution and save. Done. Don't need that coomand in the start up menu actually. It also saves when ran from terminal with the same command.

---

### Post by typos1 on 2009-06-30
But that was the point-I was setting it in the nvidia settings (I went in via preferences-display) and it would forget it everytime I booted even if it was done in a terminal. 

The only thing that worked was to put it in the startup menu. 

Its no great problem, but after I did that the date/time/volume/on+off menu started appearing in the middle of the top of the screen not at the right. And after a copl of boots the waste basket now appears in the middle of the bottm bar. I can live with it it just seems strange

---

### Post by Garyhans on 2009-06-30
Hmmmm. You did sudo nvidia-settings and it didn't save. Don't forget sudo.

---

### Post by typos1 on 2009-06-30
?

---

### Post by Garyhans on 2009-06-30
I have a Nvidia 6600gt Card. I couldn't get my setting to save unless I went to the terminal and ran gksudo nvidia-settings  It wouldn't save if I just ran it off the graphics menul

---

### Post by typos1 on 2009-06-30
I see, well the only way mine will save is if I put it in the startup menu, nothing else works!

---

### Post by Martje_001 on 2009-07-01
> **typos1 said:**
> Why should I get random moving of icons?
I don't think they're random. I think they fit in your low resolution.

I think setting the resolution (with a script) in GDM, will help. I could write a script for it. Interested?

---

### Post by typos1 on 2009-07-01
Yeah, thanks, ok. Whats GDM?

---

### Post by Martje_001 on 2009-07-02
GDM is the GNOME Display Manager, a graphical login program.

Tonight I'll have the script ready (Dutch time). I'm now going to enjoy the sun ;).

---

