---
title: "Help! Just loaded Ubuntu 9.04 and have no sound!"
date: 2009-10-13
forum: New to Ubuntu
---

### Post by southpaw83 on 2009-10-13
Hi there

I bought a new PC with no OS, and decided to give Linux a tryout. I installed Ubuntu 9.04, but I cannot get any sound to play.

I am, to be frank, a total novice at this and would appreciate someone helping me out here.

I don't even know what make my soundcard is!

---

### Post by swoody on 2009-10-13
Southpaw83 - Hello and welcome to the forums ):P

Now to make sure we check out everything - doublecheck that your speakers are plugged in, and don't have any loose connections. Also make sure that if they have a power button on them that it is powered on. Next, go to Applications>Accessories>Terminal, and in the terminal we're going to run the program:
```
alsamixer
```
Now using your arrow keys and the 'M' button, make sure all the volume levels in Alsa-mixer are turned up, and not 'muted'. If they are muted, it'll show 'MM' under the bar, rather than a number.

If you're hardware is plugged in correctly, and none of your volumes are muted, but you still don't get any sound can you give us the output of:
```
sudo lshw | grep Audio
```

---

### Post by southpaw83 on 2009-10-13
> **swoody said:**
> Southpaw83 - Hello and welcome to the forums ):P

Now to make sure we check out everything - doublecheck that your speakers are plugged in, and don't have any loose connections. Also make sure that if they have a power button on them that it is powered on. Next, go to Applications>Accessories>Terminal, and in the terminal we're going to run the program:
```
alsamixer
```Now using your arrow keys and the 'M' button, make sure all the volume levels in Alsa-mixer are turned up, and not 'muted'. If they are muted, it'll show 'MM' under the bar, rather than a number.

If you're hardware is plugged in correctly, and none of your volumes are muted, but you still don't get any sound can you give us the output of:
```
sudo lshw | grep Audio
```


Hi swoody, thanks for the reply

I managed to get alsa mixer and made sure all volume levels were turned up. Still no sound

output of sudo lshw | grep Audio is

description: Audio device
             product: 82801G (ICH7 Family) High Definition Audio Controller

---

### Post by ConXtionS on 2009-10-13
I had this same problem when I started Bro.... I had it pluged in to the wrong dang hole...  Mr Swoody here is a very smart dude.. you are in good hands.... If you dont understand something just ask him ... He will be glad to get ya on the right path.
 
 
Its a good group of dudes here that willingly give up thier time to help us noobs.... So try to rememeber not to be frustrated and learn all ya can...
 
Welcome to Linux Bro.... I hope it works great for ya.
 
Jim

---

### Post by southpaw83 on 2009-10-13
> **ConXtionS said:**
> I had this same problem when I started Bro.... I had it pluged in to the wrong dang hole...  Mr Swoody here is a very smart dude.. you are in good hands.... If you dont understand something just ask him ... He will be glad to get ya on the right path.
 
 
Its a good group of dudes here that willingly give up thier time to help us noobs.... So try to rememeber not to be frustrated and learn all ya can...
 
Welcome to Linux Bro.... I hope it works great for ya.
 
Jim

Good man Jim!

I'm willing and hoping to learn as I'm sick of Windows and like the look of Linux :)

---

### Post by zkriesse on 2009-10-13
Welcome Southpaw83, welcome. Since my good friend Swoody has already answered your question with his pure awesomeness, I will not bother to give any answers but I will tell you that you are in good hands if Swoody has answered your posts. AND WELCOME TO UBUNTU AND THE UBUNTU FORUMS!!! WOOT! :guitar:

---

### Post by ConXtionS on 2009-10-13
Mr Paw
 
While I am STILL a confirmed WINDOWS MAN.... I am trying to learn linux.... TRYING Being the operative word.
 
I dont know enough to get alot of advice yet... but I do try to help keep the frustration level down in between bouts of throwing my key board across the room and asking for help from the almighty Himself!
 
LOL
 
I hope you have some great sound now....
 
Im not sure about Mr. Zack there.... Im didnt know Mr Swoody had friends....
 
Jim

---

### Post by swoody on 2009-10-13
Well thanks guys! I don't know why you all think I'm some super-Linux-guru, but I'm flattered. I'm really nothing more than just an Ubuntu user, I just try to lend a hand when I can :)

Ok, back on topic - Southpaw83, open up System>Preferences>Sound. In the new window that appeared, under the 'Devices' tab, try the different options that are available in the drop-down menu under 'Sound Events' then after each one, click the 'Test' button to see if you can hear the test sound. Again, make sure your volume is up so you'll be able to hear the test sound.

If you still don't hear anything can you tell us if you are using a laptop, desktop, or a netbook? And more specifically the make/model?

---

### Post by southpaw83 on 2009-10-13
> **ConXtionS said:**
> Mr Paw
 
While I am STILL a confirmed WINDOWS MAN.... I am trying to learn linux.... TRYING Being the operative word.
 
I dont know enough to get alot of advice yet... but I do try to help keep the frustration level down in between bouts of throwing my key board across the room and asking for help from the almighty Himself!
 
LOL
 
I hope you have some great sound now....
 
Im not sure about Mr. Zack there.... Im didnt know Mr Swoody had friends....
 
Jim


Still no sound Jim. :(

I've been in the land of linux for about 3 hours max, and it's scary. I'm not reaching for windows yet though :P

---

### Post by southpaw83 on 2009-10-13
> **swoody said:**
> Well thanks guys! I don't know why you all think I'm some super-Linux-guru, but I'm flattered. I'm really nothing more than just an Ubuntu user, I just try to lend a hand when I can :)

Ok, back on topic - Southpaw83, open up System>Preferences>Sound. In the new window that appeared, under the 'Devices' tab, try the different options that are available in the drop-down menu under 'Sound Events' then after each one, click the 'Test' button to see if you can hear the test sound. Again, make sure your volume is up so you'll be able to hear the test sound.

If you still don't hear anything can you tell us if you are using a laptop, desktop, or a netbook? And more specifically the make/model?


Swoody, got some sound on the test, very very faint sound on rythymbox music player

---

### Post by swoody on 2009-10-13
Excellent, now we're getting somewhere :)

Click on your sound icon in the top-right of your screen, and click on the 'Volume Control' button. In the settings window that appears, click the 'Preferences' button, and make sure at least PCM and Master are selected. Then 'Close' that window.  Back in the Volume Control window, you should now see two bars named 'PCM' and 'Master' turn 'PCM' all the way up to 100%, and try the test sound again. Then from there, turn up your 'Master' volume and see if your sounds are at an acceptable level.

---

### Post by southpaw83 on 2009-10-13
> **swoody said:**
> Excellent, now we're getting somewhere :)

Click on your sound icon in the top-right of your screen, and click on the 'Volume Control' button. In the settings window that appears, click the 'Preferences' button, and make sure at least PCM and Master are selected. Then 'Close' that window.  Back in the Volume Control window, you should now see two bars named 'PCM' and 'Master' turn 'PCM' all the way up to 100%, and try the test sound again. Then from there, turn up your 'Master' volume and see if your sounds are at an acceptable level.

swoody

done as you said and the volume is still very low

---

### Post by swoody on 2009-10-13
Go back in that volume preferences window, and see if you also have an option for 'PMC2' if you do, add it to the visible bars, and make sure it's at 100% as well. Also, at the top of that window under the 'Device' drop-down menu, select the other devices, and make sure their volumes are all the way up as well. Most notably the 'device' that you were able to get the test sound working with in the System>Preferences>Sound menu.

Again, if this doesn't bring the volume to an acceptable level, please let me know :)

---

### Post by southpaw83 on 2009-10-13
> **swoody said:**
> Go back in that volume preferences window, and see if you also have an option for 'PMC2' if you do, add it to the visible bars, and make sure it's at 100% as well. Also, at the top of that window under the 'Device' drop-down menu, select the other devices, and make sure their volumes are all the way up as well. Most notably the 'device' that you were able to get the test sound working with in the System>Preferences>Sound menu.

Again, if this doesn't bring the volume to an acceptable level, please let me know :)

no luck swoody :(

---

### Post by southpaw83 on 2009-10-13
I'm going to bed just now.....I'll be back though

feel free to post suggestions

swoody, cheers for your help so far, much appreciated

---

### Post by swoody on 2009-10-13
Southpaw83 - I take it you're using a laptop? What's the make/model?

Edit: Ok well when you get a chance, we're going to try adding an option to a config file. Go to this thread here:
[http://ubuntuforums.org/showthread.php?t=1043568](http://ubuntuforums.org/showthread.php?t=1043568)
and try to find your model, or one that is very similar to it. On that list you'll see entries that look like:
> Alienware
M9750 model=6stack-dig
This means that if you have an Alienware M9750, the option we'll need to add is '6stack-dig'.

Once you find your make and model computer, we'll need to open a terminal and run:
```
gksu gedit /etc/modprobe.d/alsa-base.conf
```

In the file that opens in a new window, you'll need to add:
```
options snd-hda-intel model=xxxx
```
Where 'xxxx' is the model info that you found above. So for the example of the Alienware M9750 it would look like: "... model=6stack-dig"

Then reboot your computer, and see if your volume levels improve. If they don't look at other computers that are similar to yours on that page and try to use some of the other 'model=xxx' settings. Again, reboot after each change, and test out the new sound levels after reboot.

I really hope this takes care of your issue, but again if it doesn't work, or if you have questions feel free to let us know :)

---

### Post by southpaw83 on 2009-10-13
> **swoody said:**
> Southpaw83 - I take it you're using a laptop? What's the make/model?

its a desktop mate

its this one

[http://www.ebuyer.com/product/173624](http://www.ebuyer.com/product/173624)

---

### Post by swoody on 2009-10-13
Ah, ok. Well in the options above, I guess you're not going to find your specific model ;)

For the options I would first try adding "model=auto" and if that doesn't work "model=basic". Remember again, to reboot after each change, and test out the sound levels after restarting.

If these don't work, please let us know :)

---

### Post by EstherK on 2009-10-13
Hi, 

I recently installed ubuntu 9.04 parrallel to the vista and there is no sound on the linux side. I have sound on the Windows side though. 

I went through the forum and checked if anything is muted but nothing fixed the problem so far.

Can anybody help me - walk me through it step by step? I am an absolute beginner Ubuntu and really would like it to work properly. The computer is a new dell laptop (studio 15).

Thanks, any insight is appreciated!

---

### Post by EstherK on 2009-10-13
Oh, also, my adobe pdf reader doesn't work. I tried reinstalling it, to no avail. I can't open pdfs on this side but it works on the windows side. Any idea how to fix this?

---

### Post by southpaw83 on 2009-10-14
> **swoody said:**
> Ah, ok. Well in the options above, I guess you're not going to find your specific model ;)

For the options I would first try adding "model=auto" and if that doesn't work "model=basic". Remember again, to reboot after each change, and test out the sound levels after restarting.

If these don't work, please let us know :)

tried both swoody.....no luck

audio is still very low

---

### Post by swoody on 2009-10-14
Try out:
```
model=3stack
```
and
```
model=6stack
```
Again, be sure to reboot, and after reboot make sure the PCM and Maser volume levels are still up. If that doesn't work, start trying various "model=" settings from that page I linked. I'm really hoping this will take care of it, but if not, we may have to get an audio-guru here to help you out :)

---

### Post by Bodsda on 2009-10-14
Hi,

Could you please provide me with the output of the following command
```

lspci

```
To run that you will need to launch a terminal from the Applications > Accessories menu.

Could you also please run the following command and paste the output
```

asoundconf list

```

Kind regards,
Bodsda

p.s: Have you got any media keys on your keyboard?

---

### Post by TheStroj on 2009-10-14
Try installing these programs with Synaptic: PulseAudio Device chooser and PulseAudio Volume Control.
(if you don't know where that is, go to System - Administration - Synaptic package manager)
When you'll run them, you'll have a small icon in the top-right corner. Click on it and go to Volume Control (you can also do this by going to Applications - Sound & Video).
Try playing with settings a bit.
When you'll play some music, the music player will show up there under the playback tab. 
Right click on the bar showing how loud is the output (sorry don't know how to say this properly) and choose the output device under the 'Move stream' tab. 
It worked for me =)
Screenshot:
[http://www.shrani.si/f/1D/Un/8FZA7um/volumecontrol.png](http://www.shrani.si/f/1D/Un/8FZA7um/volumecontrol.png)

Hope this helps ;)

---

### Post by duanedesign on 2009-10-14
In order to have support for MP3 playback and decoding and support for various other audio formats (GStreamer plugins), Flash plugin, LAME (to create compressed audio files), and DVD playback install ubuntu-restricted-extras package.

Open a Terminal (Applications > Accesories > Terminal) and run the following:
```
sudo apt-get install ubuntu-restricted-extras
```

**System/Adminstration/Users and Groups**
Check that your users and root are members of the following groups. You will find a long list of groups scroll through the list and find the 3 groups below. Double click on the group and make sure your name and root are both checked. Do it for all three.

[I]pulse
pulse-access
pulse-rt[/I]

**System/Preferences/Sound**
Change everything to *PulseAudio Sound Server* except Default Mixer tracks which you should change to you hardware playback device like *Playback: HDA ATI SB ALC888 Analog*..... or something like that.

Open a Terminal (Applications > Accesories > Terminal) We are going to look for your sound cards index number. Then open alsamixer specifying the card we want to control.

in Terminal run:
```
cat /proc/asound/cards
```

Here is my output:
```
0 [NVidia         ]: HDA-Intel - HDA NVidia
```

So my card is 0 (more than likely yours will be 0 or 1)

Using your index number open alsamixer (i am using 0 in this example):
```
alsamixer -c0
```

And make sure all are turned up to a reasonable level and that none are muted. You can tell if a channel is muted because the box at the bottom will have a 'MM' instead of a '00'. You can mute/unmute by hitting the M-key. Then open Rhythmbox and try and play one of the radio stations

---

### Post by southpaw83 on 2009-10-14
> **Bodsda said:**
> Hi,

Could you please provide me with the output of the following command
```

lspci

```To run that you will need to launch a terminal from the Applications > Accessories menu.

Could you also please run the following command and paste the output
```

asoundconf list

```Kind regards,
Bodsda

p.s: Have you got any media keys on your keyboard?


lspci

00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 10)
00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 10)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
southpaw83@southpaw83-desktop:~$ 

asoundconf list


Names of available sound cards:
Intel

---

### Post by southpaw83 on 2009-10-15
bump

---

### Post by HNS-I on 2009-10-15
> **ConXtionS said:**
> I had this same problem when I started Bro.... I had it pluged in to the wrong dang hole...  Mr Swoody here is a very smart dude.. you are in good hands.... If you dont understand something just ask him ... He will be glad to get ya on the right path.
 
 
Its a good group of dudes here that willingly give up thier time to help us noobs.... So try to rememeber not to be frustrated and learn all ya can...
 
Welcome to Linux Bro.... I hope it works great for ya.
 
Jim
I just read your other post, experiencing mood swings? :p

---

