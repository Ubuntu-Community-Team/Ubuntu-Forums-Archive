---
title: "going to command line instead of gui..."
date: 2010-10-16
forum: New to Ubuntu
---

### Post by Scorcher21 on 2010-10-16
This is a continuation I think of this thread but that one says solved and mine isnt
[http://ubuntuforums.org/showthread.php?t=1570540](http://ubuntuforums.org/showthread.php?t=1570540)

 				 				**Re: Help! Ubuntu 10.04 boots to command line!** 			
 			 			 		   		 		 		Ok hate to bring up an old thread and all but he seemed to have almost exactly the same problem Im having. Except I was able to get to my gui by removing nouveau and letting my nvidia take over. But I still go straight to command line from start up though and I have to use startx to get to gui but Im having problems there. I figured Id try what either anewaguy or JKyleOKC said with the sudo cat > / etc/xorg.cof but when I attempt that through command line it says permission denied. 

Just thought of this since i can get to gui Ill try through terminal, but didnt want to have to erase all this and rewrite it in ten mins when this fails also.... not having much luck these past few days optimism is at a low.

_**EDIT:**_ OK as I figured that didnt work. I was able to do it by using nano instead of cat > but same thing once I saved and rebboted it goes to command line. And I guess I should be precise here it doesnt go directly to command line.. the screen flashes a dark green then brings up the purple ubuntu screen for like a quarter to half second then goes to commandline. Any help would be greatly appreciated.
 		                   		  		  		  		  		 		 			 				 				* 					 						[Last edited by Scorcher21]("http://ubuntuforums.org/posthistory.php?p=9981607"); 5 Minutes Ago at 09:14 AM.. 					 					 				*

---

### Post by laithbsoul on 2010-10-16
which version of Ubuntu are you running?

---

### Post by Scorcher21 on 2010-10-16
Im sorry... 10.04 

I have 10.04 on 1 HDD and 9.04 on the other which works woderfully.thats what im on now.

---

### Post by laithbsoul on 2010-10-16
so you can't use the gui at all or can you start it after you get to the command line?

---

### Post by Scorcher21 on 2010-10-16
the gui is fine sorta, when I do a startx from command line except that my network manger is missing in action and the button in top right to log on or off is completely nonfuctional. I was hoping these two issues were because it wasnt loading correctly but Im not 100% sure on that. so yes I can get to the gui and navigate away but cant access the internet o to do updates or get drivers or what have ya.

---

### Post by laithbsoul on 2010-10-16
huh, interesting. Is that what happens with a fresh install of 10.04. btw wicd is a much better network manager than the default one I've had so many problems with the default one.

---

### Post by Scorcher21 on 2010-10-16
sorry for delay talking to my dad... but yeah that is a fresh install of 10.04. Even used DBaN to completely wipe my drives to make sure no residual BS was left over. I would try the wicd however without being able to access the Internet it would be dificult to dl.

---

### Post by Old_Grey_Wolf on 2010-10-16
What do you get if you type the command ```
runlevel
```?

---

### Post by Scorcher21 on 2010-10-16
OKC tried the syslog and dmesg... dmesg goes to fast to read is there a pause break like in DOS /p? syslog just gives me an error. grey wolf Ill run that now. be back in a few.

---

### Post by laithbsoul on 2010-10-16
I'm not sure what to tell you, In the mean time to get your your internet issue fixed (hopefully). you can download a .deb file for wicd here [http://packages.ubuntu.com/lucid/all/wicd/download](http://packages.ubuntu.com/lucid/all/wicd/download) and you can just click to install on Ubuntu assuming you have a computer with access to the internet to download it but how else would you be talking to me lol :)

---

### Post by Scorcher21 on 2010-10-16
@gray wolf   the response is     N 2

@ laithbsoul....... have you not been reading? I have two HDDs with two operating systems ... 10.04, and 9.04... 9.04 which im on works fine...  I cant acess the internet on 10.04...  Im switching back and forth to troubleshoot

---

### Post by Old_Grey_Wolf on 2010-10-16
"N 2" is the correct runlevel for a graphical interface. I'll do some research for other ideas.

---

### Post by Scorcher21 on 2010-10-16
sorry for being edgy alreay worked 10 hours today.. im tired and nothings workin right.. I have to go put up 200 feet of barbed wire fence so wont be back agin today but please leave any thoughts hers and if one of em works Ill, let you know.

---

### Post by QLee on 2010-10-16
[QUOTE=Scorcher21]OKC tried the syslog and dmesg... dmesg goes to fast to read is there a pause break like in DOS /p? syslog just gives me an error. ...[/QUOTE]

You can "pipe" the command to read the log through the "more" command, this is similar to "piping" in DOS.

For example:
dmesg | more, will give you functionality like /p in DOS

cat /var/log/syslog | more

would show the syslog in a similar manner

---

### Post by JKyleOKC on 2010-10-16
At the command line, or in a terminal window, try "less /var/log/syslog" which should show you the log a page at a time. Pressing Enter will scroll by one line while pressing space will get the next page. You can also use PageUp, PageDn, and the up and down arrow keys.

The same can be done for /etc/dmesg to examine that data, and if you have a file at /var/log/xorg.0.log it will be worth while to look there also. If it's a problem with the X server, that last one will probably tell us exactly where to look for it.

If you just type "dmesg" at the command line it certainly will flash by too fast to read. Ctrl-S and Ctrl-Q are the traditional "pause" and "resume" keys, but using "less" to page the display through is much easier than trying not to miss anything on a rapid scroll.

EDIT: The difference between "less" and "more" (suggested in another message) is simply that "less" allows you to scroll backward toward the front of the file in case you want to refer back to anything while "more" only goes forward. Both programs can handle piped input as suggested in the other message, or can be given a file name as I suggested. Either way is fine.

---

### Post by Scorcher21 on 2010-10-16
Thank you OKC that was an informative response... not sure if it'll work.. way too tired for that but thank you.

---

### Post by Scorcher21 on 2010-10-17
Ok update. went through less /var/log/syslog and found a few things that may be of interest but are foreign to me.

1) The only references to gdm were: Oct 15 13:50:50 HAL Kernel : [  10.331785] type=1505 audit(128768650.564:5)operation="profile_load" pid=678 name=/usr/share/gdm/guest-session/Xsession"

and that was a few different places and times with different audit, pid and [....] numbers.

2) Oct 15 14:02:57 HAL xsession manager[9995]:WARNING: could not connect to ConsoleKit: Failed to connect to socket /var/run/dbus/system_bus_socket No such file or directory

3)@ approx 14:03 I have pages upon pages of pulseaudio failures.

I had done what OKC had suggested and wrote the /etc/xorg.conf file just as he had written out and once I saved it and tried to reboot it wouldn't let me into the gui even when i used startx through the command line. I've since gone back and commented out all the lines re-saved and rebooted. was able to get into the gui again using startx. #'s two and three may have been symptoms of that. once I get done here ill do another syslog check to see if those errors are gone.

I tried a  less /etc/dmesg & a less /var/log/xorg.0.log and got an error on both that stated no such file or directory.


_**EDIT:**_  Ok went back and checked syslog again and #'s 2 & 3 are still showing. and I still get a no such file or directory for dmesg and xorg

---

### Post by JKyleOKC on 2010-10-17
> **Scorcher21 said:**
> Ok went back and checked syslog again and #'s 2 & 3 are still showing. and I still get a no such file or directory for dmesg and xorgThe system log (syslog) is cumulative so the older errors will still be there. It can be horribly confusing when troubleshooting; you have to look near the tail end of the file to see the most recent results.

Absence of the dmesg file almost has to be due to a typing error; this file accumulates the boot-time log data up until the main system log file becomes active.

If you're getting into the GUI but don't have an xorg.0.log file, your video may be getting detected as something other than "display 0"; my system has entries for 1 and 9 in addition to 0 even though I have only one video adapter. These extra entries are apparently due to mis-detection during troubleshooting. At the command line, type "ls -l /etc/xorg*" to get a listing of all the X log files that are there, and do "less" on the one with the most recent date since that will be the one from your most recent boot.

The xorg.conf file we recommended earlier must be incompatible with your video hardware; do "sudo lshw | grep VGA" and post the output so we will know what video card you have and can then suggest changes to that simplified xorg.conf file to be compatible...

Those pulseaudio failures are pretty much normal with 10.04; you can ignore them for now. They have to do with the audio system, and if it's working just ignore them altogether. If it's not, that's a different problem!

---

### Post by Scorcher21 on 2010-10-17
ok, when I went back and checked it was the most recent i.e. @ the tail end of the list. 

i typed in exactly  "less /etc/dmesg" (without the quotes)

Ill go back now and try those other things. getting a print out may take some time since Ill have to hand write everything down from the log and transfer it over but Ill get right on that. Ill be back soon.

---

### Post by Scorcher21 on 2010-10-17
Ok 
ls -1 /etc/xorg produced the error no such file or directory. (is this because the only way I get to the gui is by using startx?)

sudo lshw | grep VGA     description: VGA compatible controller is all it says.

and oh yeah my audio isn't working... at least Ive never heard any startup sounds, but haven't tried like a CD or anything been to busy trying to get it to work and that was the least of concerns.

ahh heck thats a -l isnt it.... brb


_**EDIT:**_  ok still no such file or directory.......

---

### Post by JKyleOKC on 2010-10-17
You're looking in the wrong place. While configuration files are in /etc, the logs are in /var/log so /var/log/dmesg should work. Same for the xorg logs.

It's extremely easy to get confused. Even though I've used Linux for years I still can get myself lost when searching for a program I've just installed, or looking for documentation about something I use daily. It's definitely a case of information overload, but fortunately once you get your system working smoothly it becomes "set it and forget it."

And yes, I forgot to point out that the "-l" is a lowercase L, not a number 1 which looks identical in many fonts.

You might try "lspci" to get a list of all the known adapters; one of them should be video but might not have the letters "VGA" in its description. What we need to know is the make and model number since video is one of the areas that still are not standardized very well. The big names of makers are Nvidia, ATI, SIS, and Intel; the first two are relatively easy to work with but the last two seem to have more than their share of problems with the current software.

---

### Post by Scorcher21 on 2010-10-17
ok Ill go back and try var logs..

my card is a Geforce7300gt but Ill see what lspci says.. brb

---

### Post by Scorcher21 on 2010-10-17
ok...

/var/log/dmesg  the only reference to gdm is the same as in syslog. 

cannot find anything for xorg.... tried less /var/log/xorg    less /var/xorg  ls -l /var/log/xorg
  ls -l /var/xorg

and lspci gave me    nVidia Corporation G73 [GeForce 7300 GT] (reva2)

---

### Post by Scorcher21 on 2010-10-17
ok funny enough I can access, or at least view, my /var/log/Xorg.0.log through my file browser.. I dont see anything thats stes gdm in it either.... and come to think of It I dont think I was using a capitolX.

---

### Post by Scorcher21 on 2010-10-17
Ok problem solved. Heres what I did

went with a clean install.

on load screen hit F6 and selected nomodeset then at the end of the execution line i also added nomodeset and hit enter
During install, I made sure my name and my computers name were different than my 9.04 installation (not sure if that mattered but...) also didn't import anything from 9.04 (which I may have done before)
After install I edited out quiet splash and set it to nomodeset and started up.
Once the gui was running went into terminal and edited  /etc/default/grub changing quiet splash to nomodeset     updated the grub and tada one functioning operating system!!!!!
Thanx everyone for your patience and input have learned alot even though its seems all the errors were on my end!

---

### Post by JKyleOKC on 2010-10-18
That's good news!

I'm sorry to have given you wrong information about the X server logs. They do indeed require the capital X in the file name, and Linux is case sensitive so it does make a huge difference.

There wouldn't be any reference to "gdm" in them; the thing to look for in the Xorg* logs is any line that starts with "(EE)" indicating a serious error. Such lines can give strong hints as to the cause of the error. Of course it's all moot now since your system is up and running, but may help someone else who finds the thread in the future...

---

