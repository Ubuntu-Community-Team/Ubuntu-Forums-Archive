---
title: "Could not open location"
date: 2011-06-11
forum: New to Ubuntu
---

### Post by Crimzonblade on 2011-06-11
Hello all, I installed Ubuntu 10.10 3 days ago and have been spinning my wheels ever since. When i try to open any folder from the panel under Places, i get an error mssg. that says: Error Could not   open location 'file:///home/steve' Failed to execute child process "/media/F8F8715AF87117D8/Applications/AE1000/Linux drivers/USB   (RT2870-RT2770-RT307X-RT2070-RT357X-RT3370-RT8070-RT537X/IS_AP_STA_RT2870_D-3.2.1.0_VA-3.2.1.0_W7-3.2.1.0_RU-4.1.1.0_AU-4.1.0.0_051911_1.5.12.0WP_Free.exe" (No such file or directory) . I   deleted the file it's referring to and still get the same messg. when i try to open any folder in the Ubuntu directories. I can navigate my hard drives in Computer but not Ubuntu   directories. I've tried the following fixes i found in forums to no avail: "sudo apt-get install --fix-broken" (nothing was found broken), "ls -la ~/.update-manager-core/meta-release"   (error mssg.), "cd /home/steve/.update-manager-core" (error mssg.). I'm trying to avoid an uninstal/reinstall. Thank you in advance guys and gals!    [http://ubuntuforums.org/images/icons/icon8.gif](http://ubuntuforums.org/images/icons/icon8.gif)

---

### Post by VOT Productions on 2011-06-11
Welcome to the Ubuntu Forums! Try right clicking the entry in the file manager and then removing the file:// bit.

---

### Post by Crimzonblade on 2011-06-11
Thanks VOT, I'll give it a try. Have to switch between Windows and Ubuntu so it'll take a few minutes.

---

### Post by Crimzonblade on 2011-06-11
Please excuse my absolute newbieness, i thought you meant to click on the error window when it showed up and i'd get a dropdown menu choice to delete, i was wrong. So, I don't know what you mean by "clicking the entry? nor "removing the file:// bit". Could you please explain it like i was a child? I've worked with Windows for 14 years but I'm totally new to Linux/Ubuntu commands. Windows makes you lazy.  Thanks again VOT!

---

### Post by VOT Productions on 2011-06-11
Can you do ALT+F2 and then type nautilus?

---

### Post by Crimzonblade on 2011-06-11
Yes, I can open a Terminal with Alt+F2 but I haven't tried to start Nautius that way yet. I'll do it next. I learned after many times of opening a Terminal that way that I get the wrong Terminal I need for manipulating files. When I open a Terminal using the top panel's Accessories/Terminal, I can successfully execute some commands. I'll boot to Ubuntu then back to Windows to let you know. Windows has my Internet cnnctn. and not Ubuntu.  Thanks pardner

---

### Post by VOT Productions on 2011-06-11
Wireless internet connection? Try [linux-firmware-nonfree]("http://packages.ubuntu.com/natty/linux-firmware-nonfree").

---

### Post by Crimzonblade on 2011-06-11
Most excellent!! Something finally worked right. Starting the Nautilus browser worked great and I could navigate in the browser window without problems but I still get the error mssg. when   I try to click on folders in "Places". Kind of curious that I get an error mssg. about something that doesn't exist.

---

### Post by VOT Productions on 2011-06-11
Because it doesn't exist. Go to the places bar in Nautilus and right-click an entry (The user folder, for example) and edit entry. Then remove the file:// from the path.

---

### Post by Crimzonblade on 2011-06-11
Thank you for the firmware link VOT. I'm downloading it now. I was in the process of installing a driver I downloaded and was trying to follow the instructions I got from [http://forums.fedoraforum.org/showthread.php?t=244215](http://forums.fedoraforum.org/showthread.php?t=244215), but got stuck when I tried modifying a file which I suspected had something to do with my constant error mssg. Or, it may be because I am unable to cd to a file I have on my desktop. I've tried "cd /", "cd ", "cd /Desktop/", and all of the above with the "~" and with a / at the end of all combinations and each time, I get the "no such file" mssg. Got any clues on that little problem?

---

### Post by VOT Productions on 2011-06-11
First of all, don't use Fedora advice on your Ubuntu system.
The correct way to open a file (for example) in a terminal which is on your desktop is:

[B]cd /home/<username>/Desktop
<filename>[/B]

---

### Post by Crimzonblade on 2011-06-11
When I open Nautilus, click Places, r-click a folder to the right (assuming that's an entry), I don't get any choices to edit. R-cicking folders to the left, such as "steve" (user?), I   don't get any edit choices either, nor in Properties. Sorry for not understanding as well as I should.

---

### Post by VOT Productions on 2011-06-11
Go to your home folder, then:
Bookmarks > Add bookmark 
Press Edit Bookmarks to modify bookmarks..
Basically, you will making a shortcut to the home folder.

---

### Post by Crimzonblade on 2011-06-11
Hot dang, thanks for the advice and the cd syntax pardner! I'll make sure to pay attn. to where I get tips and for which system.

---

### Post by Crimzonblade on 2011-06-11
Giving the Edit Bookmarks a try, thanks so much for your time!

---

### Post by VOT Productions on 2011-06-11
Also, are the internet drivers installed?

---

### Post by Crimzonblade on 2011-06-11
Just read your add bookmark instructions, that's my next try...I finally realized what you were getting at; the pathname has an extra "file://" rather than just starting with a slash. Unfortunately, when I Edit Bookmarks, all the pathnames are correct   for the only 5 choices I get of Docs., Mus., Pict., Vid., or Dwnlds. The error file was in my "65 GB Files" (harddrive) and Edit Bookmarks won't let me edit that pathname.

---

### Post by Crimzonblade on 2011-06-11
I haven't gone through the research to learn how to install my Linksys AE1000 drivers yet. I've been trying to modify a file before the install as per researched-instructions. I'll also try the firmware download you gave me if the other drivers don't work.

---

### Post by VOT Productions on 2011-06-11
Try creating IS_AP_STA_RT2870_D-3.2.1.0_VA-3.2.1.0_W7-3.2.1.0_RU-4.1.1.0_AU-4.1.0.0_051911_1.5.12.0WP_Free.exe, only this time with gedit.

Save it as .exe, but leave it blank.

Also, the nonfree drivers are the best to get online if the open source ones fail.

---

### Post by Crimzonblade on 2011-06-11
Tried going to home folder and making a bookmark but the path was correct. Tried making bookmarks for harddrive and a couple others, they all had the correct paths; no extra "file://" to be found in Nautilus. Could it be in the shell?

---

### Post by VOT Productions on 2011-06-11
> **Crimzonblade said:**
> Tried going to home folder and making a bookmark but the path was correct. Tried making bookmarks for harddrive and a couple others, they all had the correct paths; no extra "file://" to be found in Nautilus. Could it be in the shell?

Can you access the bookmarks? If so, just don't use the old hard drive link.

Try my other suggestion.

---

### Post by Crimzonblade on 2011-06-11
I'm not familiar with gedit yet but I'll research it and find out how. Just to let you know, the error mssg. started right after I installed Ubuntu and tried to go to a choice under Places. After getting tired of always seeing the error, I then deleted the file; the mssg. didn't start showing up because I deleted the file.

---

### Post by Crimzonblade on 2011-06-11
Yes, I can access the bookmarks and everything works perfectly in Nautilus, it's just the top panel that produces the error mssg. I'll use Nautilus rather than the panel shortcuts. Thanks so very much for everything!! You've gotten me further than my 3 days of forum-reading and fumbling around in the os. I am truly happier than a kitty with a new litter box for all your help. Gonna spend some time on the driver thing and I'll try to post back before the day is through. Have a super nice day and take it easy my friend!!

---

### Post by VOT Productions on 2011-06-11
Note: Please use the same thread for the driver thing so I can keep track.

---

### Post by Crimzonblade on 2011-06-11
I sure will use the same thread. This is my first time posting to forums. I usually just try to find a similar problem and hope I stumble across a fix. A fix focussed on my input is fabulous!! Much quicker.

---

### Post by VOT Productions on 2011-06-11
Your welcome. It's always better to ask than search.

---

### Post by Crimzonblade on 2011-06-11
Hello everyone, I posted earlier and got some great help from VOT Productions but still need help with a Linksys AE1000 driver. I got instructions on how to make changes in a couple files, but it was from a Fedora user. I skipped the code he used and made the changes manually. Now I'm down to the last few steps: First, the Fedora user says &quot;If you are on Fedora 14 (or Kernel 2.6.35 or higher) you also need to update a few function names:&quot; Code: sed -ir -e 's/\tusb_buffer_alloc/\tusb_alloc_coherent/' -e 's/\tusb_buffer_free/\tusb_free_coherent/' include/os/rt_linux.h  Does anyone know if there is a comparable code to accomplish this for Ubuntu 10.10, Linux kernal 2.6.38.8-generic? Second, the Fedora user says &quot;Make and install:&quot; Code: make && sudo make install  Is this the correct syntax for Ubuntu? Third, the Fedora user says &quot;Create a modprobe.d config file to make sure the modules load. Should also blacklist other conflicting modules:&quot; Code: sudo su -c &quot;echo -e 'alias ra0 rt3572sta\nblacklist rt2800usb' > /etc/modprobe.d/rt3572sta.conf&quot;  Will this code work with Ubuntu also? Fourth, the Fedora user says &quot;You can add other blacklist modules, here's the list from the Ubuntu page: rt2870sta, rt2800usb, rt2860sta, rt2x00usb, rt2x00lib, rt2870sta. Now's a good time to check 'lsmod' and unload and blacklist any modules you find. Then run:&quot;" Code: sudo modprobe ra0  Is this good for Ubuntu? Fifth, the Fedora user says &quot;You should now have an ra0 device:&quot;" Code: ifconfig ra0  Can I use ifconfig with Ubuntu?  Sorry for the lengthy request but I've spent 3 days trying to figure this all out. I'm brand new to Ubuntu but worked with Windows for 14 years. Thank you in advance!

---

### Post by VOT Productions on 2011-06-12
Can you try and post the results of:

sudo ifconfig <wifi interface, normally wlan0> up

dmesg | grep -i rt2
iwconfig

---

### Post by Crimzonblade on 2011-06-12
After code: sudo ifconfig wlan0 up  I get 'wlan0: ERROR while getting interface flags: No such device'. After code: dmesg | grep -i rt2  I get no response, it just goes back to the prompt. After code: iwconfig  I get 'lo        no wireless extensions.  eth0      no wireless extensions' I've downloaded some other instructions to use with the driver I'm trying to install that will probably work, I just haven't tried them yet because I keep needing to take breaks to keep from going bonkers. Also, I downloaded linux-firmware-nonfree-1.9 driver, searched all over for a way to install it and found that it doesn't have a Read Me file or install file and ppl said to stay away from it. Synaptic didn't recognize anything in the files either. Good morning!

---

### Post by Crimzonblade on 2011-06-12
How do I insert a text box into my posts to type code into?

---

### Post by VOT Productions on 2011-06-12
This means the driver isn't installed.
To install the nonfree drivers, double click the file and when Software Center opens, double click it again. Then press install.

---

### Post by Crimzonblade on 2011-06-12
Unforunately, there doesn't seem to be any type of executable in the folder. After extraction, there are 2 folders: 1)debian, which contains a source folder with a format file and says '3.0 native' in it. There are changelog, compat, control, copyright, and rules files in debian also. 2)firmware folder with the folders broadcom, crystalhd, dvb, prism54, and prism54_softmac. Opening any of the above does nothing but show you what's inside; no type of executables at all. It's a .tar.gz file and here's a quote from a person with the same results as me '.tars without a readme and a proper uninstall should be ignored.'

---

### Post by Crimzonblade on 2011-06-12
These are the instructions I'm going to try, they're basically what I got before which I was asking about concerning code in a previous post: '1. Go to [http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2) and download &quot;RT3572USB&quot;.  2. Unzip the download to a folder.  3. Open up ./include/os/linux_rt.h in a text editor  4. Find/replace &quot;usb_buffer_alloc&quot; with &quot;usb_alloc_coherent&quot; and &quot;usb_buffer_free&quot; with &quot;usb_free_coherent&quot; respectively (there should be only 1 occurance of each)  5. Run &quot;lsusb&quot; and find the Linksys in the list (note the two hex values Example: Bus 001 Device 018: ID 13b1:002f Linksys  The &quot;hex&quot; I am talking about (in the example above) is 0x13b1 and 0x002f  6. Open terminal and go to the root of the archive that you unzipped  7. Type  sed -ir -e 's/^HAS_WPA_SUPPLICANT=n/HAS_WPA_SUPPLICANT=y/' -e 's/^HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n/HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y/' ./os/linux/config.mk  (you can copy and paste, just make sure not to include the quotation marks)  8. Type  sed -ir -e 's!^#endif // RT2870 //! {USB_DEVICE(0x13B1,0x002F)}, /* Linksys AE 1000 */\n#endif // RT2870 //!' ./common/rtusb_dev_id.c  (Replace &quot;0x13B1, 0x002F&quot; with the hex values you found in step 5. NOTE: They may be these hex values that I supplied)  9. Both step 7 and step 8 should complete without any errors (it shouldn't show any notifications of success either)  10. Type &quot;make && sudo make install&quot;  11. Restart your computer!' I've been through half of this but wondered about the code working in Ubuntu 10.10.

---

### Post by VOT Productions on 2011-06-12
Are you sure the drivers were from: [http://packages.ubuntu.com/natty/all/linux-firmware-nonfree/download](http://packages.ubuntu.com/natty/all/linux-firmware-nonfree/download)?

---

### Post by Crimzonblade on 2011-06-13
Remarkably intuitive question!! I must have used a different location the first time because I got the file linux-firmware-nonfree-1.9 the first time. This time I got the file   linux-firmware-nonfree_1.9_all.deb. Unfortunately, package managers don't work with either version and I haven't tried using the terminal to cd to target folder, make, sudo make install,   sudo modprobe, iwconfig on the .deb file. Is that the way to install this .deb file? In the mean time, I had success downloading 2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO.bz2 from   [http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2) and using the latter code.

---

### Post by VOT Productions on 2011-06-13
Right... cd to your path where you downloaded it, and run dpkg -i linux-firmware-nonfree_1.9_all.deb

---

### Post by Crimzonblade on 2011-06-13
On a side note, I discovered that MS Windows created a pathname to another file i downloaded that had the same 'file://' beginning that my original problem file had. Since Windows created it and it carried over a problem to Ubuntu, I'll have to research how to resolve the problem in Windows; Ubuntu is exonerated.

---

### Post by Crimzonblade on 2011-06-13
Excellent! I don't have to 'make' it or type 'sudo' or anything?

---

### Post by VOT Productions on 2011-06-13
No. That's compiling. Debs are "packages" pre-built.
For example, when you type sudo apt-get install wine1.3, it gets the deb of Wine 1.3, and it installs it using dpkg.
Did it work?

---

### Post by Crimzonblade on 2011-06-14
I haven't tried it yet. I'm wanting to uninstall the previous driver first so there isn't any conflict. It seems like you are generally on in the morning and early afternoon so I'm going to open another thread requesting help to uninstall 2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO. in hopes of finding someone else who's as helpful as you. I tried to tackle the uninstall using Ubuntu Software Center and Synaptic Package Manager but failed. Thank you a thousand times for all your help and patience!!

---

