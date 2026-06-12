---
title: "Bluetooth headphones as Ubuntu's Speakers?"
date: 2007-08-08
forum: Networking &amp; Wireless
---

### Post by bigOlogN on 2007-08-08
Hello,

[LIST]
[*]I have the [_Motorola S9's_]("http://www.motorola.com/motoinfo/product/details.jsp?globalObjectId=177").

[*]I have a [_USB Bluetooth dongle_]("http://global.mobileaction.com/product/product_Bluetooth_730.jsp").

[*]I have Ubuntu 7.04.
[/LIST]
Now the :?:.

How can I use the S9 as wireless headphones for my computer?  I currently only use the S9 with my phone ([_Samsung Sync_]("http://www.samsung.com/us/consumer/detail/detail.do?group=mobilephones&type=mobilephones&subtype=att&model_cd=SGH-A707DAACIN")).  Does anyone know?

Thanks,
bigOlogN

---

### Post by wieman01 on 2007-08-08
You might try using XMMS... Pretty sure it will work out. I can listen to music via Bluetooth using my Plantronics 590 headset.

---

### Post by jerich007 on 2007-09-07
i have the s9 headphones too.  trying to use them with the built-in bluetooth on my IBM T43 laptop.  No luck yet.  I tried checking the bluez.org project for help, but couldn't make out how to get started.  i have bluez-utils and bluetooth is active on my laptop.  i can pair them with my laptop, but no sounds.  any help is appreciated.

- J

---

### Post by wieman01 on 2007-09-07
> **jerich007 said:**
> i have the s9 headphones too.  trying to use them with the built-in bluetooth on my IBM T43 laptop.  No luck yet.  I tried checking the bluez.org project for help, but couldn't make out how to get started.  i have bluez-utils and bluetooth is active on my laptop.  i can pair them with my laptop, but no sounds.  any help is appreciated.

- J
No sound via Skype?

---

### Post by priegog on 2007-09-10
I too have a motorola S9... 
I am very interested in this subject too... any help would be awesome.

---

### Post by cmartintx on 2007-09-20
Hell I haven't figured it out completely, but I've made some progress here. 

I've got S9's like you guys and a T-Mobile Dash that I'm trying to sync with evolution... so far things look grim. I'm still a n00b so I'm using howto's. The following have gotten me most of th e way there: Ubuntu sees the headset, but I can't pair, the headphones or play audio through XMMS.

Setting up an audio gateway to have full system output through the headphones would be rad.

These have helped me:
[http://bluetooth-alsa.sourceforge.net/build.html](http://bluetooth-alsa.sourceforge.net/build.html)
 on this one I get hung up at:

create ~/.asoundrc with simply:

      pcm.a2dpd {
            type a2dpd
      }

and I can't run a2dpd as instructed. 


[https://help.ubuntu.com/community/BluetoothSetup?highlight=%28CategoryBluetooth%29](https://help.ubuntu.com/community/BluetoothSetup?highlight=%28CategoryBluetooth%29)
This one is good for basic bluetooth info if y'all haven't stumbled upon it already.

Sadly it looks like there's a lot more support for this technology under KDE

Keep posting any info you find!

---

### Post by Student Driver on 2007-11-11
Is this getting any further?  All I get is the following error when I try to browse the device and connect:

```
"obex://[bl:ue:to:ot:h]" is not a valid location.
```

My T-Mobile Dash is bonded via BT to my laptop, and I can pass files back and forth just fine.  However, I can't get the laptop to link with the headset.

---

### Post by Student Driver on 2007-11-11
OK, I got it working using the referenced article ([http://wiki.bluez.org/wiki/HOWTO/AudioDevices#SupportedPlayers](http://wiki.bluez.org/wiki/HOWTO/AudioDevices#SupportedPlayers)) and this command from another thread:

```
sudo hidd --connect aa:bb:cc:dd:ee:ff
```

After that command, the bluetooth applet prompted for the OBEX passkey and then the bond occured.  After that, I ran the gconf command at the link above and got the audio re-routed.  So, it works, but:

[LIST=1]
[*]It prompts for the OBEX key again
[*]The sound lags by about a second or so
[/LIST]

So, not a bad start but I might poke around a bit and see what's up with the lag.  If it's something to do with the USB dongle, then it's fixable by just swapping it out.

---

### Post by priegog on 2007-11-12
> **Student Driver said:**
> OK, I got it working using the referenced article ([http://wiki.bluez.org/wiki/HOWTO/AudioDevices#SupportedPlayers](http://wiki.bluez.org/wiki/HOWTO/AudioDevices#SupportedPlayers)) and this command from another thread:

```
sudo hidd --connect aa:bb:cc:dd:ee:ff
```

After that command, the bluetooth applet prompted for the OBEX passkey and then the bond occured.  After that, I ran the gconf command at the link above and got the audio re-routed.  So, it works, but:

[LIST=1]
[*]It prompts for the OBEX key again
[*]The sound lags by about a second or so
[/LIST]

So, not a bad start but I might poke around a bit and see what's up with the lag.  If it's something to do with the USB dongle, then it's fixable by just swapping it out.

Hi. To do all of this graphically, you may want to download a program called blueman at [http://blueman.tuxfamily.org/index.php?option=com_content&view=article&id=51&Itemid=56](http://blueman.tuxfamily.org/index.php?option=com_content&view=article&id=51&Itemid=56)
it also saves the passkey so you don't need to enter it again. Hope that helps.

---

### Post by John Jason Jordan on 2007-11-17
> **priegog said:**
> Hi. To do all of this graphically, you may want to download a program called blueman at [http://blueman.tuxfamily.org/index.php?option=com_content&view=article&id=51&Itemid=56](http://blueman.tuxfamily.org/index.php?option=com_content&view=article&id=51&Itemid=56)
it also saves the passkey so you don't need to enter it again. Hope that helps.
I found out about blueman in another thread, and it is great. Using it I have been able to get my Sony DR-BT50 headphones paired up. However, I can't get sound out of them. I am using them with a Lenovo T61 Thinkpad (brand new, with Gutsy amd64) and the bluetooth seems to be working fine. Sound also works fine, as far as the built in speakers and the headphone jack. The problem is how to tell ALSA or whatever runs the sound system on Gutsy to send the sound output to whatever the bluetooth connection is called instead of to the speakers and/or headphone jack.

If I open the volume control I can go into File > Change Device and it now lists "BT Headset (Alsa mixer)." Selecting that gives me a panel with Master and Microphone. I set them all the way up, but still nothing out of the headphones. If I go into Preferences I can add AGC and Loopback as items to be visible. Doing so, and checking them, does not help.

I wish I knew more about how sound works. I'm sure it's just a question of setting the right options, but there are too many choices and I don't know what most of them do. Does anyone have any suggestions?

---

### Post by John Jason Jordan on 2007-11-18
Follow-up on how I got sound out of my new Sony DR-BT50 bluetooth headphones. Bluetooth is working fine and I managed to get the headphones paired up using Blueman. Blueman is not in the Ubuntu repositories, but you can download it and install it with Gdebi. However, although I got the headphones paired up fine, for a long time I couldn't get sound (e.g., from Rhythmbox) out of the headphones instead of the speakers or the headphone jack. I found the secret here:

[http://wiki.bluez.org/wiki/HOWTO/AudioDevices#Alsaconfiguration](http://wiki.bluez.org/wiki/HOWTO/AudioDevices#Alsaconfiguration)

I had to make a file ~/.asoundrc and put into it:

pcm.bluetooth {
	type bluetooth
	device 00:13:A9:B2:82:5F
}

Where the device is the address listed in Blueman. 

After getting the headphones paired up I found another item in the volume control dialog box. Previously under File > Change Device it listed "HDA Intel (Alsa mixer)" and "Analog Devices AD1984 (OSS Mixer)." Now there is a new one, "BT Headset (Alsa Mixer)." After checking it and making the .asoundrc file the headphones are working perfectly. The sound from these headphones is awesome. If you are a serious music fan you won't be disappointed.

I also have the volume buttons working (since flashing the BIOS). They work fine for controlling the sound from the speakers and the headphone jack, but they don't have any effect on the headphones. Oh well, the volume controls on the headphones work fine, and that is all I need.

---

### Post by priegog on 2007-11-18
Holy **** you hit the jackpot. 
I had to do some extra configs on amarok (as the linked page says) for it to play on the headphones, but it is working!!! You gotta make either a wiki entry or a how-to, preferably both. It's got its kinks (for instance an incoming skype chat screwed it for some reason), but with the community they can be worked out eventually. 
I'm glad I did not give up on this thread and unsubscribe, Thanks a lot man!!!
BTW if you want to delegate the writing of the how-to's just say so.

---

### Post by John Jason Jordan on 2007-11-20
> **priegog said:**
> Holy **** you hit the jackpot. 
I had to do some extra configs on amarok (as the linked page says) for it to play on the headphones, but it is working!!! You gotta make either a wiki entry or a how-to, preferably both. It's got its kinks (for instance an incoming skype chat screwed it for some reason), but with the community they can be worked out eventually. 
I'm glad I did not give up on this thread and unsubscribe, Thanks a lot man!!!
BTW if you want to delegate the writing of the how-to's just say so.
I've discovered a kink or two as well. First, it doesn't want to stay connected. You have to go through a sequence of click here, click there, push that button, push this button, all in the right order. 

But my big problem is that I can't get RealPlayer to send sound out the headphones. RealPlayer stubbornly insists on sending the sound out the speakers or headphone jack. RealPlayer works fine otherwise, however. Rythmbox, on the other hand, works fine with the bluetooth headphones. Unfortunately, Rhythmbox sucks at playing streaming radio broadcasts.

---

### Post by priegog on 2007-11-21
> **John Jason Jordan said:**
> I've discovered a kink or two as well. First, it doesn't want to stay connected. You have to go through a sequence of click here, click there, push that button, push this button, all in the right order. 

But my big problem is that I can't get RealPlayer to send sound out the headphones. RealPlayer stubbornly insists on sending the sound out the speakers or headphone jack. RealPlayer works fine otherwise, however. Rythmbox, on the other hand, works fine with the bluetooth headphones. Unfortunately, Rhythmbox sucks at playing streaming radio broadcasts.

Yes, exactly. I've only been able to make it work with amarok (which is all I need), because I have to make the extra configuration within amarok in the xine engine to use the bluetooth headset.  I've only found this kind of configuration in kde applications (amarok, kaffeine, etc) which is less than ideal, but as I said, amarok is all I need. What did you have to do to get it working in rythmbox?
Also, for streaming audio (including realplayer) I've found mplayer to do an acceptable (not great tho) job, so if you can make that work with your headphones that might be an option.

---

### Post by John Jason Jordan on 2007-11-21
> **priegog said:**
> Yes, exactly. I've only been able to make it work with amarok (which is all I need), because I have to make the extra configuration within amarok in the xine engine to use the bluetooth headset.  I've only found this kind of configuration in kde applications (amarok, kaffeine, etc) which is less than ideal, but as I said, amarok is all I need. What did you have to do to get it working in rythmbox?
Also, for streaming audio (including realplayer) I've found mplayer to do an acceptable (not great tho) job, so if you can make that work with your headphones that might be an option.
I just installed Amarok, in the hopes that it would solve my problems. However, something must be wrong with the installation. It won't play any of the MP3 files that I ripped from CDs (and which play fine on my iPod and with everything else). When I try to do so it pops up a message that Amarok currently cannot play MP3 files and asks if I want to install the necessary utilities to do so. I click on OK, it installs some stuff (in the background so I can't see what it actually did), then says Amarok needs to be restarted. So I restart it, try to play an MP3 and it repeats the same routine. And it won't play any streaming radio stations. I tried about a dozen of the stations that were preinstalled and for every single one it popped up an error message saying the format was not supported. Why would the links be preinstalled if they don't work? There must be something missing in my installation. I used Synaptic to install it.

As for Rhythmbox and the headphones, it just worked. Once the headphones were turned on and paired, sound from Rhythmbox just came out of the headphones automatically. However, that was yesterday. Today (after restarting a few times due to trips to the university and back) Rhythmbox won't play anything. If I try to play something, either an MP3 or a streaming radio station, it just locks up. I suspect that all the installing and uninstalling of other media players has messed up something that it needs. I did a complete reinstall, but it's still messed up. And that may also be what is wrong with Amarok, although at least Amarok doesn't lock up.

I need to figure out what the dependencies of these things are and get the basic stuff working before I continue. Unfortunately, all I know is Synaptic.

---

### Post by John Jason Jordan on 2007-11-21
I finally got Amarok fixed so it works OK, except none of the streaming radio preselections work. Not one of them. I usually get "No suitable demux plugin. This often means that the file format is not supported." I've also installed several other media players. Streamtuner seems to work, although it pops up xmms to do the playing. Still, nothing works as well as RealPlayer.

Right now I want to figure out how to get the headphones to stay paired up. I'm using Blueman for the configuration and getting them paired up is maddening. Once in a while I actually get them working. For some reason I am unable to memorize exactly the sequence of things I do when I succeed so that I can repeat it next time. Here is what I do:

Launch Blueman
Hold down the button on the headphones (these are the DR-BT50) until I see the pink and blue lights both flashing continuously.
In Blueman click on Inquiry. This finds the device and lists it properly.
In Blueman, click on Unbond, then on Bond. This opens a little Bonding window asking for a passkey. I enter 0000 (from the instructions that came with the headphones) and click on OK. A balloon pops up saying that bonding was successful and in Blueman the line showing the headphones shows a 100% icon. And then instantly another balloon pops up saying the device disconnected. The headphones are no longer showing the pink and blue lights. Instead I get a blue light flashing twice as fast as it does when it remains connected. After about five minutes the headphones turn themselves off.
If I open the volume control I do not see the device as an option. I think that is the secret, but I can't get the volume control open fast enough before the device disconnects. If I could I think it would list the device and I could select it. Yet on several occasions I did manage to get it to connect and stay connected. I just can't remember how I did it.

---

### Post by priegog on 2007-11-22
> **John Jason Jordan said:**
>  Here is what I do:

Launch Blueman
Hold down the button on the headphones (these are the DR-BT50) until I see the pink and blue lights both flashing continuously.
In Blueman click on Inquiry. This finds the device and lists it properly.
In Blueman, click on Unbond, then on Bond. This opens a little Bonding window asking for a passkey. I enter 0000 (from the instructions that came with the headphones) and click on OK. A balloon pops up saying that bonding was successful and in Blueman the line showing the headphones shows a 100% icon. And then instantly another balloon pops up saying the device disconnected. The headphones are no longer showing the pink and blue lights. Instead I get a blue light flashing twice as fast as it does when it remains connected. After about five minutes the headphones turn themselves off.
If I open the volume control I do not see the device as an option. I think that is the secret, but I can't get the volume control open fast enough before the device disconnects. If I could I think it would list the device and I could select it. Yet on several occasions I did manage to get it to connect and stay connected. I just can't remember how I did it.

Ok, now let me help you simplify things. I don't use the same headphones, but I presume it will be the same steps. 
First, you have to know that it's not necessary fr you to unbond and bond your headphones every time, that is exactly the kind of behavior that blueman came to save us from, because unlike every other single app out there, it remembers the pairings and the devices. So your setting up from now on should be something like this:

1, 2 & 3 (the order doesn't really matter in these 3 steps) plug in bluetooth  dongle, fire up blueman and turn the headphones on (but not all the 6 seconds you do it to get them in pairing mode, just 3 seconds so that it only turns on and only the blue lights blinks). Optional: if you have used the headphones with your mobile phone since the last time you used it with your computer, either turn the phone off or disconnect them using the phone menu.
4 Open the blueman window and click the second button, the one that says "list seen", now your headphones icon should appear; click once on that icon.
5 Go to the menu Services>Headset Connection and then click on the connect button. It will ask you for your root password and then you can close both windows.
6 Now double click on the volume icon and select the bluetooth device, and from now on you know the steps. 

It's interesting from this point on that it remains in a kind of standby mode, and when an application requests the service it automatically connects. For example, if I turn amarok on, it will use the stereo profile, but if I use skype it will connect with the headset profile.

Hope that helps, and I'm glad you got amarok fixed, as my internet connection hasn't been the most reliable so I couldn't help you in time. You did do it installing xine-mp3 (or whatever that's called) right?

---

### Post by John Jason Jordan on 2007-11-22
> **priegog said:**
> Ok, now let me help you simplify things. I don't use the same headphones, but I presume it will be the same steps. 
First, you have to know that it's not necessary fr you to unbond and bond your headphones every time, that is exactly the kind of behavior that blueman came to save us from, because unlike every other single app out there, it remembers the pairings and the devices. So your setting up from now on should be something like this:

1, 2 & 3 (the order doesn't really matter in these 3 steps) plug in bluetooth  dongle, fire up blueman and turn the headphones on (but not all the 6 seconds you do it to get them in pairing mode, just 3 seconds so that it only turns on and only the blue lights blinks). Optional: if you have used the headphones with your mobile phone since the last time you used it with your computer, either turn the phone off or disconnect them using the phone menu.
4 Open the blueman window and click the second button, the one that says "list seen", now your headphones icon should appear; click once on that icon.
5 Go to the menu Services>Headset Connection and then click on the connect button. It will ask you for your root password and then you can close both windows.
6 Now double click on the volume icon and select the bluetooth device, and from now on you know the steps. 

It's interesting from this point on that it remains in a kind of standby mode, and when an application requests the service it automatically connects. For example, if I turn amarok on, it will use the stereo profile, but if I use skype it will connect with the headset profile.

Hope that helps, and I'm glad you got amarok fixed, as my internet connection hasn't been the most reliable so I couldn't help you in time. You did do it installing xine-mp3 (or whatever that's called) right?
Thanks a bunch! That really helps. Now all that remains is to get something that will play streaming radio stations, or figure out how to get RealPlayer to send the sound to the bluetooth headphones instead of the speakers. Everything else sends sounds to the headphones, just RealPlayer has a problem with bluetooth devices. I've had some luck with Streamtuner, but when I click to start a radio station it launches xmms for the actual playing. Xmms has a really ugly interface on the Gnome desktop. I can probably fix the xmms visual appearance, but first I need to figure out the different ways that radio stations stream. Even RealPlayer can't play all the stations that I try. However, part of the problem is that I've noticed it stores the URL in /tmp. Once I restart the computer all those URLS are gone. Lame.

I also acquired a bluetooth mouse (Logitech V270) and got it working fine. However, I notice that if I am using the headphones and move or click the mouse I frequently get an interruption in the music. I'd like to figure out whether this is fixable or not and, if so, how.

Amarok says it can't play MP3s, in spite of the fact that I have installed every codec and utility I can find. Plus, Amarok annoyingly is not UTF-8, so my MP3s show up with strange characters for all the letters that have diacritics. Supposedly you can fix this in the settings by changing the font, but that didn't do anything. That is, I changed the font, but the appearance did not even change to the font I selected.

At this point I've gone back to Rhythmbox for playing MP3s, and I'm trying to get it to play streaming radio stations. I've found that it plays any station where the URL ends in .m3u. However, it can't play those that end in .rm, .rpm or .smil, which is most of the ones that I have bookmarked in RealPlayer. I may be able to fix them by going to mikesradioworld.com and picking a different choice, as most stations stream in more than one format. It would be great to get Rhythmbox doing all my music playing so I can forget about all the others.

---

### Post by priegog on 2007-11-22
Well, about the issue with the mouse, you could try filing a bug to bluez which is the group that develops the bluetooth part of linux. 
You seem to be happy with rythmbox, but try one last thing first: go to synaptic and install these 2 packages: libxine1 and libxine1-plugins, and see if that helps amarok play your mp3 files. From what I read it may also make it play the streams (altho most probably not the realplayer kind, but who knows?)
Hope that helps

---

### Post by havier on 2007-11-22
> **John Jason Jordan said:**
> 
I had to make a file ~/.asoundrc and put into it:

pcm.bluetooth {
	type bluetooth
	device 00:13:A9:B2:82:5F
}

Where the device is the address listed in Blueman. 


Excuse my ignorance, I'm a complete newby. How and where did you make that file?

I'm very interested in making my Motorola DC800 audio adapter work under Ubuntu 7.10 and still I hadn't any success.

---

### Post by John Jason Jordan on 2007-11-22
> **havier said:**
> Excuse my ignorance, I'm a complete newby. How and where did you make that file?
I'm very interested in making my Motorola DC800 audio adapter work under Ubuntu 7.10 and still I hadn't any success.
You need the address of the adapter first. You can get that various ways. I use Blueman, which is not in the Ubuntu repositories, but you can download it and install it with Gdebi package installer. Once you have Blueman installed and running, turn on your adapter and click on Scan in Blueman. When Blueman finds the adapter it will list the address.

Next, open Text Edit (gedit) and paste this code:

```
pcm.bluetooth {
type bluetooth
device 00:13:A9:B2:82:5F <- this is the address you have to change for your adapter
}

```

Save the file in your home folder as .asoundrc. Don't forget to put the . in front.

---

### Post by John Jason Jordan on 2007-11-22
> **priegog said:**
> Well, about the issue with the mouse, you could try filing a bug to bluez which is the group that develops the bluetooth part of linux. 
You seem to be happy with rythmbox, but try one last thing first: go to synaptic and install these 2 packages: libxine1 and libxine1-plugins, and see if that helps amarok play your mp3 files. From what I read it may also make it play the streams (altho most probably not the realplayer kind, but who knows?)
Hope that helps
That did help. Actually, libxine1 was already installed, but not libxine1-plugins. And when I went to install libxine1-plugins it wanted to install half a dozen additional libraries. I let it go ahead and install them all. Afterwares Amarok was able to play my MP3s. So that was worth doing, even though I'm happy with Rhythmbox. 

Regarding radio stations, I've discovered that I can play a lot of them in Rhythmbox, enough to keep me satisfied. I listen to almost nothing but classical, and I use the lists from mikesradioworld.com and from [http://publicradiofan.com](http://publicradiofan.com). In some cases a station will offer more than one format. So far I have about 40 stations working, which is plenty to satisfy me. However, if I try any station where the stream ends in .asx it will crash Rhythmbox dead. I also can't get anything ending in .rm, .rpm, .ram, .smi or .smil to play. I think the .r* ones are RealPlayer formats, which ought to be supported on Linux.

Neither Amarok nor Rhythmbox are very stable. If a user tries a format that is not supported it shouldn't just crash. But Rhythmbox is OK as long as I use only stations that I know will work.

I'll deal with the mouse issue later. Thanks for the tip about libxine1-plugins.

---

### Post by John Jason Jordan on 2007-11-22
> **John Jason Jordan said:**
> I'll deal with the mouse issue later. Thanks for the tip about libxine1-plugins.
Mouse issue partially resolved. After rebooting the bluetooth mouse did not work until the entire desktop was loaded, at which time it worked perfectly without needing any fiddling. And now the mouse still causes the sound to cut out, but much less than before. It does not cut out just with moving around, an occasional click, etc. It cuts out only if I select a large bunch of text.

---

### Post by priegog on 2007-11-23
> **John Jason Jordan said:**
> Mouse issue partially resolved. After rebooting the bluetooth mouse did not work until the entire desktop was loaded, at which time it worked perfectly without needing any fiddling. And now the mouse still causes the sound to cut out, but much less than before. It does not cut out just with moving around, an occasional click, etc. It cuts out only if I select a large bunch of text.

Good to hear. However file the bug anyways so this gets looked into.

---

### Post by John Jason Jordan on 2007-11-23
> **priegog said:**
> Good to hear. However file the bug anyways so this gets looked into.
Will do.

However, bad stuff continues. I had Rhythmbox working fine, although it would crash if I tried to open a streaming radio station where the stream ended in .ram, .rm, .rpm, .smi, .smil or .asx. I had about 40 stations and was going through to make sure they always worked. A few did not and I deleted them. But I had bunch more to try out, so I added about ten more. Now, Rhythmbox will crash if you look at it cross-eyed, so I would close it down periodically to force it to save the new playlist settings. (There is no Save button.) Suddenly when I tried to relaunch it I got an error message that its database could not be read and it refused to launch. Renaming the database (which contained hours of work entering my radio stations) was the only way to get it back. Of course, now I get to start all over again from the beginning. Considering that it will probably let me spend several more hours getting it reconfigured, then **** me again, I decided to try other options instead. Rhythmbox is just too buggy. I mean, if a user tries to launch a stream that is not supported, you give the user an error message; you don't crash, destroy their work and refuse to launch.

So first I went back to Amarok, but for some reason I couldn't play MP3s any more. It was working after I installed libgxine1 and -plugins, but something must have messed it up. The libgxine1 files are still installed, but Amarok refuses to play MP3s. I reinstalled everything, but no joy. 

Then I tried a lot of other options, and nothing works at all. Banshee appears to play things, but no sound. Exaile just locks up upon launching it. Xmms and beep have a horrible interface and can't do radio, although they do play and I do get sound. 

Finally, I uninstalled everything. Then I reinstalled Amarok and libgxine1 and -plugins, but now it hangs a long time when I launch it and then gives me "xine was unable to initialize any audio drivers." And if I try to play something it hangs. And the display is messed up as it always was.

And through it all, RealPlayer still works perfectly - plays all streams and all MP3 files. It's just that it can't send the sound to the bluetooth headphones.

The problem is that there are a zillion libraries and codecs and I don't want to spend the next month of my life studying which one does what. I look at wikis and how-tos and most of them are hopelessly out of date - recommending libraries and files that haven't been used for years, sending you to websites that no long exist. Someone needs to make a wiki specifically for Gutsy and include exactly how to get different kinds of multimedia files and streams to work with each of the available programs.

Here's another example of my frustration. When I first installed Gutsy (a fresh install on a brand new computer) I could play movies with Totem. Well, that is now broken as well. Totem says it doesn't have the right configuration files, but is silent as to what it needs. So I installed mplayer. And mplayer plays a DVD movie just fine, but without sound. So then I installed VLC media player. VLC plays DVDs just fine, complete with sound. Thinking that mplayer and VLC player might have added codecs or something, I restarted the computer and tried totem and mplayer again. No change. Totem still won't even try to play the movie and mplayer plays it without sound. How can this be? Don't they all use the same codecs and libraries? This stuff is too confusing. If a program is supposed to play a certain type of media it should install everything it needs. OK, end of rant. I'll shut up now.

I'm going to bed. May-be this stuff will make more sense in the morning.

---

### Post by priegog on 2007-11-23
> **John Jason Jordan said:**
>  I mean, if a user tries to launch a stream that is not supported, you give the user an error message; you don't crash, destroy their work and refuse to launch.

Agreed
> **John Jason Jordan said:**
> So first I went back to Amarok, but for some reason I couldn't play MP3s any more. It was working after I installed libgxine1 and -plugins, but something must have messed it up. The libgxine1 files are still installed, but Amarok refuses to play MP3s. I reinstalled everything, but no joy. 

Then I tried a lot of other options, and nothing works at all. Banshee appears to play things, but no sound. Exaile just locks up upon launching it. Xmms and beep have a horrible interface and can't do radio, although they do play and I do get sound. 

Finally, I uninstalled everything. Then I reinstalled Amarok and libgxine1 and -plugins, but now it hangs a long time when I launch it and then gives me "xine was unable to initialize any audio drivers." And if I try to play something it hangs. And the display is messed up as it always was.
All right, I have a few ideas to get amarok working, but you'll have to get dirty and use the terminal instead of synaptic. What we'll do is usea command that is designed to remove the program and it's dependencies, and then remove the configuration files, so that you'll then have a truly like-new amarok installation. Feel free to adapt these commands to rythmbox or whatever other program you want to try this on. 
```
sudo apt-get autoremove amarok xine libxine1 libxine1-plugins
```
now (since i believe you like things to be graphical), go to your home directory, and hit Ctrl+h. that will show hidden folders. Now navigate to .kde/share/apps/ and delete the amarok directory. Now your computer is as if amarok was never installed. And now it's time to reinstall everything. I'll give you a command but feel free to use synaptic for this one.
```
sudo apt-get install amarok xine libxine1 libxine-plugins
```
Now try everything again, first with the normal speakers and then with the headset (so as to determine where the problem(s) lie).
> **John Jason Jordan said:**
> The problem is that there are a zillion libraries and codecs and I don't want to spend the next month of my life studying which one does what. I look at wikis and how-tos and most of them are hopelessly out of date - recommending libraries and files that haven't been used for years, sending you to websites that no long exist. Someone needs to make a wiki specifically for Gutsy and include exactly how to get different kinds of multimedia files and streams to work with each of the available programs.
Agreed, but "someone" doesn't exist so once we figure this one out we should contribute by either doing a how-to here in the forums or putting up/modifying a wiki entry

> **John Jason Jordan said:**
> Here's another example of my frustration. When I first installed Gutsy (a fresh install on a brand new computer) I could play movies with Totem. Well, that is now broken as well. Totem says it doesn't have the right configuration files, but is silent as to what it needs. So I installed mplayer. And mplayer plays a DVD movie just fine, but without sound. So then I installed VLC media player. VLC plays DVDs just fine, complete with sound. Thinking that mplayer and VLC player might have added codecs or something, I restarted the computer and tried totem and mplayer again. No change. Totem still won't even try to play the movie and mplayer plays it without sound. How can this be? Don't they all use the same codecs and libraries? This stuff is too confusing. If a program is supposed to play a certain type of media it should install everything it needs. OK, end of rant. I'll shut up now.

I'm going to bed. May-be this stuff will make more sense in the morning.
As far as I know, totem and mplayer DO use some sort of system-wide codecs (even tho I believe they are different ones). VLC, on the other hand, uses it's own codecs and does not share them. Great little program, isn't it? 
Now, as fr the codecs, try to install these packages (if you don't have them already). You will need the universe and multiverse repositories I believe (if you don't know how to do it, just ask).
-gstreamer0.10-plugins-base
-gstreamer0.10-plugins-good
-gstreamer0.10-plugins-bad-multiverse
-gstreamer0.10-plugins-ugly  (I know the naming convention is hilarious)
-gstreamer0.10-plugins-ugly-multiverse
-libgstreamer0.10-0
-totem-gstreamer
-libxine1-misc-plugins
-libxine1-ffmpeg
-ubuntu-restricted-extras
-kubuntu-retricted-extras
Sorry for the long list, but I just went over synaptic and put what I saw there. Most probably when you install one of these a bunch of the rest will get marked too. Anyways give it a go.

---

### Post by John Jason Jordan on 2007-11-23
Thanks for the detailed reply.

First, I did this:
sudo apt-get autoremove amarok xine libxine1 libxine1-plugins

That went OK, so then I did this:
jjj@Devil7:~$ sudo apt-get install amarok xine libxine1 libxine-plugins
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package xine is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package xine has no installation candidate

Noting that it could not find xine, I checked my repositories. I have under Ubuntu software:
Canonical-supported Open Source Software (main)
Community-maintained Open Source Software (universe)
Proprietary drivers for devices (restricted)
Software restricted by copyright or legal issues (multiverse)
and under Third-Party Software I have:
[http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
[http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner (source)
[http://archive.canonical.com/](http://archive.canonical.com/) gutsy partner
[http://apt.wicd.net](http://apt.wicd.net) feisty extras

I don't know what the last line referring to feisty is doing in there. I added the CD, but after reloading I still can't find xine. Searching in Synaptic for "xine" I found a few suspicious ones that were not installed: amarok-xine, gxine, gxineplugin, totem-gstreamer, totem-xine and xine-plugin. I installed them all, but still no joy. Amarok launches but still says xine could not find any audio drivers. And interestingly, deleting the .kde/share/amarok folder didn't delete everything, as after reinstalling it the playlist was still there. (I keep all my MP3s in /jjj, not in /home/jjj because I don't want them backed up every time I back up ~/.) 

Then (using Synaptic) I looked for:
-gstreamer0.10-plugins-base
-gstreamer0.10-plugins-good
-gstreamer0.10-plugins-bad-multiverse
-gstreamer0.10-plugins-ugly (I know the naming convention is hilarious)
-gstreamer0.10-plugins-ugly-multiverse
-libgstreamer0.10-0
-totem-gstreamer
-libxine1-misc-plugins
-libxine1-ffmpeg
-ubuntu-restricted-extras
-kubuntu-retricted-extras

They were all installed, but I marked them to be reinstalled. 

Right now Amarok launches, finds all the MP3s but won't play anything. It insists that xine cannot find a suitable audio driver.

Rhythmbox launches, sees all my MP3s - radio list file renamed, so all it sees now are the MP3s. It appears to allow me to play an MP3, but nothing happens. There is no progress when I click on the play button.

Totem insists it cannot play a movie.

Mplayer plays a movie, but no sound.

RealPlayer continues to play radio streams, but cannot find the bluetooth headphones.

VLC plays movies, MP3s and radio, through the speakers or the bluetooth headphones. However, its interface is confusing. It can't see my MP3s except if I add them one at a time to its playlist. And it takes forever before it starts to play something, even an MP3 right on my hard disk.

I suspect the problems with Amarok and Rhythmbox is that xine is not installed. Why I cannot find it is a mystery. Synaptic lists 22,840 packages. I'm sure I have every possible repository.

If I ever get this figured out I will make a long documentation of what went wrong and how I fixed it.

---

### Post by priegog on 2007-11-23
Sorry about the whole xine thing, it doesn't exist for me either (just checked). I pretty much pulled it out of my a** for the command, but it seemed logical at the time.
I'm intrigued as to what your problem is. It seems to be screwed up all over the place, because neither amarok or rythmbox (in the short time that I've used it) seem buggy or incomplete at all in my experience. 
I'm also intrigued by the fact that amarok remembered your playlists and such... (however we can be pretty sure that's my fault for not knowing rather than it being some weird bug)
The last repository is for the program wicd (a replacement for network manager), you may have installed it in the past and forgot about it, or some wireless setup script may have set that up (if I recall correctly), so don't worry about it.
I'm sorry I can't be of any more help. I'm still learning my way through linux so... I suppose you could try and do a clean reinstall <ducks>. I know this is not the way things should (or would be required to) be fixed in linux, but it IS the easier way. But if you do that, the doubt of what was going on will haunt you in your dreams forever.

---

### Post by John Jason Jordan on 2007-11-23
> **priegog said:**
> Sorry about the whole xine thing, it doesn't exist for me either (just checked). I pretty much pulled it out of my a** for the command, but it seemed logical at the time.
I'm intrigued as to what your problem is. It seems to be screwed up all over the place, because neither amarok or rythmbox (in the short time that I've used it) seem buggy or incomplete at all in my experience. 
I'm also intrigued by the fact that amarok remembered your playlists and such... (however we can be pretty sure that's my fault for not knowing rather than it being some weird bug)
The last repository is for the program wicd (a replacement for network manager), you may have installed it in the past and forgot about it, or some wireless setup script may have set that up (if I recall correctly), so don't worry about it.
I'm sorry I can't be of any more help. I'm still learning my way through linux so... I suppose you could try and do a clean reinstall <ducks>. I know this is not the way things should (or would be required to) be fixed in linux, but it IS the easier way. But if you do that, the doubt of what was going on will haunt you in your dreams forever.
Thanks for all your help and suggestions. I'm not going to do a clean install. For one thing, I need this computer working for at least another couple of weeks until fall term at the university is over. I don't have time right now. Moreover, everything else continues to work perfectly. I'll just keep poking at stuff until I figure out how to fix it. At the moment I'm thinking of turning my efforts toward figuring out why RealPlayer cannot send sound to the bluetooth headphones, when everything else can. If I could get that fixed I would pretty much forget about the rest of the problems, as RealPlayer handles all the radio and MP3 formats without a problem.

I should also add that I found that VLC can play streaming radio, including the .asx format that nothing else (except RealPlayer) can do. I only discovered that a few hours ago. VLC has a really confusing interface, but maybe if I live in it long enough I'll figure it out. As for Amarok, I find it annoying because you can't delete the preinstalled links, not to mention the messed up fonts. Rhythmbox has left a bad taste in my mouth. The rest are not worth trying to fix.

Thanks for your help and patience. Maybe someone else will chime in with a brilliant suggestion that will help.

---

### Post by pudland on 2007-11-25
blueman tells me the headset address is connected when pressing play.
I hear a beep and static through headset when using vlc or beep media player.


 $  sudo a2dpd
A2DPD[20:54:56.702]: init_ipc: Selected IPC: unix, addr=127.0.0.1, bcst=127.0.0.255, port=21453
A2DPD[20:54:56.704]: main: a2dpd [Sep 29 2007 16:10:15] starting ...
A2DPD[20:54:56.704]: main: (errno=9:Bad file descriptor)a2dpd addr=00:0C:55:9C:ED:FF timer=0 us [Sep 29 2007 16:10:15]
A2DPD[20:54:56.704]: a2dpd_signal_init: Getting on DBUS
A2DPD[20:54:56.708]: a2dpd_signal_init: Installing watch
A2DPD[20:54:56.708]: add_dbus_watch: Added watch 0 0x80a2930 disabled
A2DPD[20:54:56.708]: add_dbus_watch: Added watch 1 0x80a2958 enabled
A2DPD[20:54:56.708]: a2dpd_signal_init: Registering object path: /com/access/a2dpd
A2DPD[20:54:56.708]: a2dpd_signal_init: Acquiring service: com.access.a2dpd
A2DPD[20:54:56.710]: a2dpd_signal_init: OK
A2DPD[20:54:56.710]: a2dpd_signal_init: OK
A2DPD[20:54:56.710]: a2dpd_register_sdp: Start
A2DPD[20:54:56.710]: add_avrtg: 
A2DPD[20:54:56.710]: add_a2source: 
A2DPD[20:54:56.710]: a2dpd_register_sdp: OK
A2DPD[20:54:56.710]: main_loop: 
A2DPD[20:54:56.710]: make_server_socket: 
A2DPD[20:54:56.710]: a2dpd_signal_state: Started 00:0C:55:9C:ED:FF
A2DPD[20:54:56.710]: bta2dpdevicenew: 
A2DPD[20:54:56.710]: a2dpd_signal_address_changed: 00:0C:55:9C:ED:FF
A2DPD[20:54:56.711]: a2dpd_signal_set_socket: Signal socket set to 7
A2DPD[20:54:56.711]: a2dpd_signal_state: Disconnected 
A2DPD[20:54:56.712]: a2dp_alloc: 
A2DPD[20:54:56.712]: a2dp_alloc: (a2dp = 0x80a62f0)
A2DPD[20:54:56.712]: a2dp_new: 00:0C:55:9C:ED:FF, 8000
A2DPD[20:54:56.712]: a2dp_new: State AVDTP_STATE_DISCONNECTED
A2DPD[20:54:56.712]: alsa_new: 
A2DPD[20:54:56.712]: alsa_new: device=plughw:0,0, framerate=8000
A2DPD[20:54:56.712]: alsa_new: State ALSA_STATE_DISCONNECTED
A2DPD[20:54:56.712]: alsa_new: returning 0x80a8488
A2DPD[20:54:56.712]: sco_new: 
A2DPD[20:54:56.712]: sco_new: State SCO_STATE_DISCONNECTED
A2DPD[20:54:56.712]: sco_state_disconnect: Filtering state : already disconnected
A2DPD[20:54:56.712]: main_loop: Bluetooth Device Settings [8000 hz, 1 channels, 16 bits]
A2DPD[20:54:56.712]: init_uinput: (errno=2:No such file or directory)Cannot open /dev/input/uinput
A2DPD[20:54:56.713]: avrcp_new: Listening for AVRCP on socket 9
A2DPD[20:54:56.713]: avrcp_new: 0x80a8598


$  btsco -v 00:0C:55:9C:ED:FF
btsco v0.42
Device is 1:0
Voice setting: 0x0060
RFCOMM channel 2 connected
Using interface hci0
speaker volume: 11 mic volume: 11
i/o needed: connecting sco...
connected SCO channel
Done setting sco fd
recieved AT+CKPD=200
speaker volume: 11 mic volume: 11
driver is not in use
disconnected SCO channel
speaker volume: 11 mic volume: 11
i/o needed: connecting sco...
connected SCO channel
Done setting sco fd
recieved AT+CKPD=200
speaker volume: 11 mic volume: 11


$  arecord --verbose -D plughw:Headset test2.wav
Recording WAVE 'test2.wav' : Unsigned 8 bit, Rate 8000 Hz, Mono
Plug PCM: Linear conversion PCM (S16_LE)
Its setup is:
  stream       : CAPTURE
  access       : RW_INTERLEAVED
  format       : U8
  subformat    : STD
  channels     : 1
  rate         : 8000
  exact rate   : 8000 (8000/1)
  msbits       : 8
  buffer_size  : 4000
  period_size  : 1000
  period_time  : 125000
  tick_time    : 4000
  tstamp_mode  : NONE
  period_step  : 1
  sleep_min    : 0
  avail_min    : 1000
  xfer_align   : 1000
  start_threshold  : 1
  stop_threshold   : 4000
  silence_threshold: 0
  silence_size : 0
  boundary     : 2097152000
Slave: Hardware PCM card 1 'BT Headset' device 0 subdevice 0
Its setup is:
  stream       : CAPTURE
  access       : MMAP_INTERLEAVED
  format       : S16_LE
  subformat    : STD
  channels     : 1
  rate         : 8000
  exact rate   : 8000 (8000/1)
  msbits       : 16
  buffer_size  : 4000
  period_size  : 1000
  period_time  : 125000
  tick_time    : 4000
  tstamp_mode  : NONE
  period_step  : 1
  sleep_min    : 0
  avail_min    : 1000
  xfer_align   : 1000
  start_threshold  : 1
  stop_threshold   : 4000
  silence_threshold: 0
  silence_size : 0
  boundary     : 2097152000


$ modinfo snd_bt_sco
filename:       /lib/modules/2.6.20-16-generic/kernel/ubuntu/misc/snd-bt-sco.ko
license:        GPL
description:    Bluetooth SCO Headset Soundcard
author:         Jonathan Paisley <jp@dcs.gla.ac.uk>
srcversion:     E0F63CCD7351B3BE9FDB95A
depends:        snd-pcm,snd-page-alloc,snd,snd-hwdep
vermagic:       2.6.20-16-generic SMP mod_unload 586 
parm:           index:Index value for Bluetooth SCO Headset Soundcard. (array of int)

$  sudo hciconfig hci0 revision
Password:
hci0:   Type: USB
        BD Address: 00:16:CF:F9:5F:31 ACL MTU: 1017:8 SCO MTU: 64:8
        Firmware 218.65 / 130

---

### Post by Ron F. on 2007-12-19
Dear People,

Following the directions in this thread, I was able to get my Motorola S9 headset working with Amarok. It seems like a kludge however, as I could only get it to work by setting Amarok's Configuration -> Engine -> xine Engine -> ALSA device configuration -> Stereo to Bluetooth.

I could not bond using Blueman, as it crashed every time I tried to use it to bond to the S9, so I did that using the command line. After bonding, and trusting, trying to avoid the damn obex error messages, etc., I then used Blueman to change the profile from headset to sink, and then it worked. I had the necessary lines in .asoundrc of course. It worked well enough to work repeatedly across turning off then back on the S9 and restarting Ubuntu.

I was never able to get Skype 2.0 to work with the S9 headset, and finally gave up on that. I don't know where the problem is, maybe Skype. I tried to force the headset profile, using Blueman - no help. I have not tried forcing "voice" in .asoundrc yet, maybe that would do it. When selecting any of the Bluetooth related devices in Skype's options, the best I can do is crash Skype!

I tried using asoundconf to select the Bluetooth Headset as the default card, but that makes no difference. Same with forcing Bluetooth in the Gnome Sound preferences. All the tests result in a deafening silence.

What would be acceptable someday, is if I could use the ****** Bluetooth headset after it has been bonded, trusted, and then connected, (whatever) by selecting Headset (and do it on the fly) as the default sound card, say by using asoundconf-gtk (or something similar,) and have it just work!!!

It is only sensible to leave Amarok's and Skype's sound devices pointing to "default", rather than "Bluetooth." What a concept.

Then, maybe the following would  be possible.... I am puttering around the house with my stereo Bluetooth headset on, listening to Radio Paradise streaming through Amarok, when all of a sudden, a Skype call comes in! I hit a button on the side of the headset, and take the call. During the call, Amarok mutes! After the call is completed,  and my friend hangs up, Amarok continues to play again..........

Fantasy.

-Ron

---

### Post by priegog on 2007-12-19
Yes, it is unfortunate the state in which bluetooth development is on Linux.
The worst part is... it's probably REALLY simple to do what you described (provided you got it all working in the first place), requiring no more than a simple script that plugs into the skype API. (maybe built into blueman?).
As I said, it's a really sad thing that the most advanced bluetooth management app in Linux (blueman) is not being actively developed.

---

### Post by Troca on 2008-06-20
i got my sony DB Bt50 with amarok after reading you guide thanks alot :)

---

### Post by error420 on 2008-07-04
> **priegog said:**
> Yes, it is unfortunate the state in which bluetooth development is on Linux.
The worst part is... it's probably REALLY simple to do what you described (provided you got it all working in the first place), requiring no more than a simple script that plugs into the skype API. (maybe built into blueman?).
As I said, it's a really sad thing that the most advanced bluetooth management app in Linux (blueman) is not being actively developed.

It IS sad. Bluetooth headsets only seem to work in specific Audio applications. Why can't the bluetooth be the primary audio device for all apps? What about when you want to play games or open other applications besides amarok and the other media players? :( . There has to be a simple way of doing this without changing this and changing that.

---

