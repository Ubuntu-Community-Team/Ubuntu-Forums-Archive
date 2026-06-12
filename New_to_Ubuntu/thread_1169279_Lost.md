---
title: "Lost"
date: 2009-05-25
forum: New to Ubuntu
---

### Post by Leshinsky on 2009-05-25
Ok,  here is what i have.  I am using a dual boot from wubi-installer.  I have Ubuntu (i believe on a partition) and windows xp.  i have been using ubuntu and like it so far.  so i am trying to get some pictures from xp, and of course i got a virus on it.  when i boot up i get this error:
STOP: c0000221 unknown hard error
\systemroot\system32.dll

I looked all through windows forums and the only way they say to fix this is to be in windows. (or a hardware problem which it could be a driver in windows, but not hardware is messed up cuz it all works in ubuntu, which i am using now on the same computer).  so my question is does anyone know a way to fix this from ubuntu, (registary error) or is there a way i can pull my files over without getting into windows (through ubuntu) since i want to get rid of windows anyways.

---

### Post by Bölvaður on 2009-05-25
wubi installes ubuntu on a file on your windows partition (I think), it is part of the windows ecosystem.

If you'd have done normal install you could just drag and drop files from ubuntu to xp. this really seem like a windows problem to me, never seen anything like this (it looks windows like)

---

### Post by mike555 on 2009-05-25
A wubi install is an install of Linux inside windows, not on a separate partition.......... you should back up all your stuff on to a thumbdrive or external harddrive and just reinstall Ubuntu , this time by starting your computer from the cd and using the whole harddrive (wiping Windows ) if this is what you want .........

---

### Post by Leshinsky on 2009-05-25
Ok,  this is what i have.  i did this
**[How to Access Windows Files in Ubuntu]("http://www.wikihow.com/Access-Windows-Files-in-Ubuntu")**

					    One of the biggest difficulties migrating to Ubuntu is losing access to your windows files. Fortunately, it is not too difficult to overcome this...but read the warnings before trying this out. All that is needed is to mount the windows partition after you boot into Ubuntu. Of course, the first problem is determining which partition contains the windows files.
        [[COLOR=#006398]**_Windows Protection_**[/COLOR]]("http://googleads.g.doubleclick.net/aclk?sa=l&ai=BEIlSrEMaSvaHGJfijATC5KjcBaT24nXo6ODWCcCNtwGAsOoBEAEYASCYv48FKAQ4AFDOn5bPBmDJppeN6KSMGKAB4u-l_gOyAQ93d3cud2lraWhvdy5jb226AQk0Njh4NjBfYXPIAQHaATVodHRwOi8vd3d3Lndpa2lob3cuY29tL0FjY2Vzcy1XaW5kb3dzLUZpbGVzLWluLVVidW50dYACAcgC-LSYB6gDAegD4AXoAwXoA68C6APhBfUDAAAABA&num=1&sig=AGiWqtxigfInBE6lwm9-bGUSPhdFcvLyFg&client=ca-pub-9543332082073187&adurl=http://www.microsoft.com/forefront/en/us/trial-software.aspx")
[COLOR=#000000]Protect information & control access with free trial downloads![/COLOR]
[COLOR=#006398][www.Microsoft.com/Forefront]("http://googleads.g.doubleclick.net/aclk?sa=l&ai=BEIlSrEMaSvaHGJfijATC5KjcBaT24nXo6ODWCcCNtwGAsOoBEAEYASCYv48FKAQ4AFDOn5bPBmDJppeN6KSMGKAB4u-l_gOyAQ93d3cud2lraWhvdy5jb226AQk0Njh4NjBfYXPIAQHaATVodHRwOi8vd3d3Lndpa2lob3cuY29tL0FjY2Vzcy1XaW5kb3dzLUZpbGVzLWluLVVidW50dYACAcgC-LSYB6gDAegD4AXoAwXoA68C6APhBfUDAAAABA&num=1&sig=AGiWqtxigfInBE6lwm9-bGUSPhdFcvLyFg&client=ca-pub-9543332082073187&adurl=http://www.microsoft.com/forefront/en/us/trial-software.aspx")[/COLOR][[COLOR=#006398]**_Windows Terminal Server_**[/COLOR]]("http://googleads.g.doubleclick.net/aclk?sa=l&ai=BJg6nrEMaSvaHGJfijATC5KjcBf2o-ooBx-zu-QzAjbcBoMzrARACGAIgmL-PBSgEOABQwc_ym_r_____AWDJppeN6KSMGLIBD3d3dy53aWtpaG93LmNvbboBCTQ2OHg2MF9hc8gBAdoBNWh0dHA6Ly93d3cud2lraWhvdy5jb20vQWNjZXNzLVdpbmRvd3MtRmlsZXMtaW4tVWJ1bnR1qAMB6APgBegDBegDrwLoA-EF9QMAAAAE&num=2&sig=AGiWqtyMuzpazDVw3WvfvadXu7xytJHPzg&client=ca-pub-9543332082073187&adurl=http://www.jigantic.com")
[COLOR=#000000]low prices fast, friendly and reliable service[/COLOR]
[COLOR=#006398][www.jigantic.com]("http://googleads.g.doubleclick.net/aclk?sa=l&ai=BEIlSrEMaSvaHGJfijATC5KjcBaT24nXo6ODWCcCNtwGAsOoBEAEYASCYv48FKAQ4AFDOn5bPBmDJppeN6KSMGKAB4u-l_gOyAQ93d3cud2lraWhvdy5jb226AQk0Njh4NjBfYXPIAQHaATVodHRwOi8vd3d3Lndpa2lob3cuY29tL0FjY2Vzcy1XaW5kb3dzLUZpbGVzLWluLVVidW50dYACAcgC-LSYB6gDAegD4AXoAwXoA68C6APhBfUDAAAABA&num=1&sig=AGiWqtxigfInBE6lwm9-bGUSPhdFcvLyFg&client=ca-pub-9543332082073187&adurl=http://www.microsoft.com/forefront/en/us/trial-software.aspx")[/COLOR][[COLOR=#006398]**_Troubleshooting Windows Xp_**[/COLOR]]("http://googleads.g.doubleclick.net/aclk?sa=l&ai=Bj-earEMaSvaHGJfijATC5KjcBej78MgB6Ozl7wzAjbcB8IeHAhADGAMgmL-PBSgEOABQ6NfJtQVgyaaXjeikjBiyAQ93d3cud2lraWhvdy5jb226AQk0Njh4NjBfYXPIAQHaATVodHRwOi8vd3d3Lndpa2lob3cuY29tL0FjY2Vzcy1XaW5kb3dzLUZpbGVzLWluLVVidW50dcgC2vWjCqgDAegD4AXoAwXoA68C6APhBfUDAAAABA&num=3&sig=AGiWqtzcysI5tCeZiqxQOBdGBhF_4dJbNw&client=ca-pub-9543332082073187&adurl=http://m1339.ic-live.com/698/%3F39804572%26OVMTC%3Dcontent%26site%3Dwww.wikihow.com%26creative%3D3360845056%26OVKEY%3Dtroubleshooting%2520windows%2520xp")
[COLOR=#000000]In-home & phone support for your PC w/Embarq RescueIT Protection Plan[/COLOR]
[COLOR=#006398][RescueIT.Embarq.com]("http://googleads.g.doubleclick.net/aclk?sa=l&ai=BEIlSrEMaSvaHGJfijATC5KjcBaT24nXo6ODWCcCNtwGAsOoBEAEYASCYv48FKAQ4AFDOn5bPBmDJppeN6KSMGKAB4u-l_gOyAQ93d3cud2lraWhvdy5jb226AQk0Njh4NjBfYXPIAQHaATVodHRwOi8vd3d3Lndpa2lob3cuY29tL0FjY2Vzcy1XaW5kb3dzLUZpbGVzLWluLVVidW50dYACAcgC-LSYB6gDAegD4AXoAwXoA68C6APhBfUDAAAABA&num=1&sig=AGiWqtxigfInBE6lwm9-bGUSPhdFcvLyFg&client=ca-pub-9543332082073187&adurl=http://www.microsoft.com/forefront/en/us/trial-software.aspx")[/COLOR][[COLOR=#006398]**_Virtual Dedicated Server_**[/COLOR]]("http://googleads.g.doubleclick.net/aclk?sa=l&ai=BhcazrEMaSvaHGJfijATC5KjcBbqRmY4BqNH3zQrAjbcBkPGVAxAEGAQgmL-PBSgEOABQjZX8jwdgyaaXjeikjBigAa6H4f4DsgEPd3d3Lndpa2lob3cuY29tugEJNDY4eDYwX2FzyAEB2gE1aHR0cDovL3d3dy53aWtpaG93LmNvbS9BY2Nlc3MtV2luZG93cy1GaWxlcy1pbi1VYnVudHWAAgGoAwHoA-AF6AMF6AOvAugD4QX1AwAAAAQ&num=4&sig=AGiWqtyhzQx0sdFAOtqBG0aLFjvqjWMJHQ&client=ca-pub-9543332082073187&adurl=http://www.opusinteractive.com/managed-hosting/vclustr-virtuals/index.html%3F_kk%3Dlinux%2520virtualization%26_kt%3Dba330358-d7b6-46ac-aa9f-2bf529653a25")
[COLOR=#000000]VDS/VPS Windows or Linux Servers. 24/7 Support. Service Guarantee![/COLOR]
[COLOR=#006398][www.OpusInteractive.com]("http://googleads.g.doubleclick.net/aclk?sa=l&ai=BEIlSrEMaSvaHGJfijATC5KjcBaT24nXo6ODWCcCNtwGAsOoBEAEYASCYv48FKAQ4AFDOn5bPBmDJppeN6KSMGKAB4u-l_gOyAQ93d3cud2lraWhvdy5jb226AQk0Njh4NjBfYXPIAQHaATVodHRwOi8vd3d3Lndpa2lob3cuY29tL0FjY2Vzcy1XaW5kb3dzLUZpbGVzLWluLVVidW50dYACAcgC-LSYB6gDAegD4AXoAwXoA68C6APhBfUDAAAABA&num=1&sig=AGiWqtxigfInBE6lwm9-bGUSPhdFcvLyFg&client=ca-pub-9543332082073187&adurl=http://www.microsoft.com/forefront/en/us/trial-software.aspx")[/COLOR][RIGHT][[IMG]http://pagead2.googlesyndication.com/pagead/abglogo/abg-en-100c-000000.png[/IMG]]("http://services.google.com/feedback/abg?url=http://www.wikihow.com/Access-Windows-Files-in-Ubuntu&hl=en&client=ca-pub-9543332082073187&adU=www.Microsoft.com/Forefront&adT=Windows+Protection&adU=www.jigantic.com&adT=Windows+Terminal+Server&adU=RescueIT.Embarq.com&adT=Troubleshooting+Windows+Xp&adU=www.OpusInteractive.com&adT=Virtual+Dedicated+Server&done=1")[/RIGHT]
  Hide these ads
  
      
  Show Ads  
       **[[edit]("http://www.wikihow.com/index.php?title=Access-Windows-Files-in-Ubuntu&action=edit&section=1")] Steps**

 
[LIST=1]
[*]Install [COLOR=green]**gparted**[/COLOR] ([COLOR=green]**System &#8594; Administration &#8594; Synaptics Package Manager**[/COLOR] &#8594; search for gparted, mark it for installation and, when it installs, run it from [COLOR=green]**System &#8594; Partition Editor**[/COLOR]). Look for an NTFS partition – it is likely to be the one windows is on.
[*]Having located the partition, write down the name – it will look something like [COLOR=green]**/dev/hda2**[/COLOR]. Do this carefully – this is no time for dyslexia. Now check to see if this is the partition by manually mounting it and looking at the files.
[*]Open a terminal ([COLOR=green]**Application &#8594; Accessories &#8594; Terminal**[/COLOR]) and make yourself root by typing [COLOR=green]**sudo -s**[/COLOR] and pressing enter. You will be prompted for the root password and will then become root. Being root assumes that you know what you are doing – you could easily cause disaster if you make a mistake, so concentrate. Carefully type this line at the prompt and press enter
[*]mkdir /mnt/windows
[*]You may replace [COLOR=green]**/mnt/windows**[/COLOR] with [COLOR=green]**/mnt/windrv**[/COLOR] or any other name you prefer. Now, having created the directory that is going to hold your windows files, type the following command carefully at the prompt and press enter
[*]mount -t ntfs /dev/sda2 /mnt/windows -o "umask=022"
[*]Make sure you replace [COLOR=green]**/dev/sda2**[/COLOR] with the name of the windows partition you wrote down. Now access the mounted drive and ensure that you can read the files by going to [COLOR=green]**Places &#8594; Computer**[/COLOR] and navigating to [COLOR=green]**/mnt/windows**[/COLOR]. If you can see your files, you are all set. If not, you've mounted the wrong drive, unmount it using [COLOR=green]**umount /dev/sda2**[/COLOR], making sure that you use the correct name for your drive.
[/LIST]
 

 
     **[[edit]("http://www.wikihow.com/index.php?title=Access-Windows-Files-in-Ubuntu&action=edit&section=2")] Tips**

 
[LIST]
[*]Now, you will probably want to have the computer boot up and automatically mount the windows drive so you can save files back and forth seamlessly. This is easily achieved via a script that loads at startup. The commands in the script will have to be run with root permissions, so you will have to save the file in [COLOR=green]**/etc/init.d**[/COLOR]. You are going to use the same command you used manually. Most of the other lines in the script are comments.
[*]Start a text editor as root by typing [COLOR=green]**gedit /etc/init.d/mountwinfs.sh**[/COLOR]. Copy the lines below into the text editor and save it as [COLOR=green]**/etc/init.d/mountwinfs.sh**[/COLOR].
[*]!/bin/bash
[*]BEGIN INIT INFO
[*]Provides: mountwinfs
[*]Required-Start: $local_fs
[*]Required-Stop:
[*]Default-Start: S
[*]Default-Stop:
[*]Short-Description: Mount the windows file system
[*]Description: Mount the windows file system
[*]END INIT INFO
[*]mount -t ntfs /dev/sda2 /mnt/windows -o “umask=022&#8243;
[*]Do not forget to replace [COLOR=green]**/dev/sda2**[/COLOR] with the name of the windows partition you wrote down. Also, don't forget to replace [COLOR=green]**/mnt/windows**[/COLOR] with whatever you decided to call the directory. Save the file.
[*]The file will be owned by root. You need to set permissions for the file, so it can be executed as follows.
[*]chmod +x mountwinfs.sh
[*]Now you need to convince Ubuntu to run this file at startup. This is done using the command below.
[*]update-rc.d mountwinfs.sh defaults
[*]This command will create links to start the script at runlevels 2, 3, 4, 5 and links to stop it at runlevels 0, 1, 6 (halt, single user and reboot runlevels)
[*]Now to test what you have done...close all windows and restart the computer. Open the file browser ([COLOR=green]**Places &#8594; Computer**[/COLOR]), navigate to [COLOR=green]**/mnt/windows**[/COLOR] and make sure you can see your files.
[*]Your final task is to make a link to [COLOR=green]**/mnt/windows**[/COLOR] on your desktop. Doing this through your file manager is not easy, since you are not root and you only "own" files at your home directory and below. As before, open up your terminal ([COLOR=green]**Application &#8594; Accessories &#8594; Terminal**[/COLOR]) and make yourself root by typing [COLOR=green]**sudo -s**[/COLOR] and pressing enter. You will be prompted for the root password and will then become root. Enter the following command to create the link to your folder.
[*]ln -s /mnt/windows ~/Desktop
[*]You should now have ready access to your windows files every time you log in.
[/LIST]
_______________________________________________________________________________

I do have access to my windows files.  i guess i have to wait til i can afford a external hard drive. cuz i got over a hundred gigs of stuff to back up.  but like i said i can get into windows files.  so in my error i found the ntdll.dll file.  downloaded a new one from [www.dll-files.com](www.dll-files.com).  deleated the old one and installed the new one.  before when i was trying to load windows i would see their welcome screen then it would reset.  i pulled the error and it was that file.  now it just sits on the welcome screen.  so im lost again.  but atleast i got my files.  so if i did a system restore from my windows disk i would lose everything right.  even ubuntu.  i have a 2 gig flash drive.  can i fit just ubuntu on this.  and when i get a external hd i can do the rest.  i think there is a virus in windows.  i dont know how well the ubuntu virus scanner will work.  but now that i have the windows "disk" open in ubuntu i can virus scan windows through ubuntu right.

---

### Post by Ms_Angel_D on 2009-05-25
Basically what has happend is your trying to perform opertations that would require you have an actual Ubuntu install. You don't have that you have a Wubi install. Which is Ubuntu installed onto a virtual disk in your windows install. So it seems to me you have messed up your windows install trying to perform this action.

At this point I recommend using a live cd to back up and save any important files you might want/need from windows, then re-installing windows. 

if you would like a separate partition for your Ubuntu install have a look at [this tutorial]("http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm") with screenshots.

Else you can just do a full ubuntu install from the live cd.

---

### Post by anewguy on 2009-05-25
> **Leshinsky said:**
> Ok,  this is what i have.  i did this
**[How to Access Windows Files in Ubuntu]("http://www.wikihow.com/Access-Windows-Files-in-Ubuntu")**

					    One of the biggest difficulties migrating to Ubuntu is losing access to your windows files. Fortunately, it is not too difficult to overcome this...but read the warnings before trying this out. All that is needed is to mount the windows partition after you boot into Ubuntu. Of course, the first problem is determining which partition contains the windows files.
        [[COLOR=#006398]**_Windows Protection_**[/COLOR]]("http://googleads.g.doubleclick.net/aclk?sa=l&ai=BEIlSrEMaSvaHGJfijATC5KjcBaT24nXo6ODWCcCNtwGAsOoBEAEYASCYv48FKAQ4AFDOn5bPBmDJppeN6KSMGKAB4u-l_gOyAQ93d3cud2lraWhvdy5jb226AQk0Njh4NjBfYXPIAQHaATVodHRwOi8vd3d3Lndpa2lob3cuY29tL0FjY2Vzcy1XaW5kb3dzLUZpbGVzLWluLVVidW50dYACAcgC-LSYB6gDAegD4AXoAwXoA68C6APhBfUDAAAABA&num=1&sig=AGiWqtxigfInBE6lwm9-bGUSPhdFcvLyFg&client=ca-pub-9543332082073187&adurl=http://www.microsoft.com/forefront/en/us/trial-software.aspx")
[COLOR=#000000]Protect information & control access with free trial downloads![/COLOR]
[COLOR=#006398][www.Microsoft.com/Forefront]("http://googleads.g.doubleclick.net/aclk?sa=l&ai=BEIlSrEMaSvaHGJfijATC5KjcBaT24nXo6ODWCcCNtwGAsOoBEAEYASCYv48FKAQ4AFDOn5bPBmDJppeN6KSMGKAB4u-l_gOyAQ93d3cud2lraWhvdy5jb226AQk0Njh4NjBfYXPIAQHaATVodHRwOi8vd3d3Lndpa2lob3cuY29tL0FjY2Vzcy1XaW5kb3dzLUZpbGVzLWluLVVidW50dYACAcgC-LSYB6gDAegD4AXoAwXoA68C6APhBfUDAAAABA&num=1&sig=AGiWqtxigfInBE6lwm9-bGUSPhdFcvLyFg&client=ca-pub-9543332082073187&adurl=http://www.microsoft.com/forefront/en/us/trial-software.aspx")[/COLOR][[COLOR=#006398]**_Windows Terminal Server_**[/COLOR]]("http://googleads.g.doubleclick.net/aclk?sa=l&ai=BJg6nrEMaSvaHGJfijATC5KjcBf2o-ooBx-zu-QzAjbcBoMzrARACGAIgmL-PBSgEOABQwc_ym_r_____AWDJppeN6KSMGLIBD3d3dy53aWtpaG93LmNvbboBCTQ2OHg2MF9hc8gBAdoBNWh0dHA6Ly93d3cud2lraWhvdy5jb20vQWNjZXNzLVdpbmRvd3MtRmlsZXMtaW4tVWJ1bnR1qAMB6APgBegDBegDrwLoA-EF9QMAAAAE&num=2&sig=AGiWqtyMuzpazDVw3WvfvadXu7xytJHPzg&client=ca-pub-9543332082073187&adurl=http://www.jigantic.com")
[COLOR=#000000]low prices fast, friendly and reliable service[/COLOR]
[COLOR=#006398][www.jigantic.com]("http://googleads.g.doubleclick.net/aclk?sa=l&ai=BEIlSrEMaSvaHGJfijATC5KjcBaT24nXo6ODWCcCNtwGAsOoBEAEYASCYv48FKAQ4AFDOn5bPBmDJppeN6KSMGKAB4u-l_gOyAQ93d3cud2lraWhvdy5jb226AQk0Njh4NjBfYXPIAQHaATVodHRwOi8vd3d3Lndpa2lob3cuY29tL0FjY2Vzcy1XaW5kb3dzLUZpbGVzLWluLVVidW50dYACAcgC-LSYB6gDAegD4AXoAwXoA68C6APhBfUDAAAABA&num=1&sig=AGiWqtxigfInBE6lwm9-bGUSPhdFcvLyFg&client=ca-pub-9543332082073187&adurl=http://www.microsoft.com/forefront/en/us/trial-software.aspx")[/COLOR][[COLOR=#006398]**_Troubleshooting Windows Xp_**[/COLOR]]("http://googleads.g.doubleclick.net/aclk?sa=l&ai=Bj-earEMaSvaHGJfijATC5KjcBej78MgB6Ozl7wzAjbcB8IeHAhADGAMgmL-PBSgEOABQ6NfJtQVgyaaXjeikjBiyAQ93d3cud2lraWhvdy5jb226AQk0Njh4NjBfYXPIAQHaATVodHRwOi8vd3d3Lndpa2lob3cuY29tL0FjY2Vzcy1XaW5kb3dzLUZpbGVzLWluLVVidW50dcgC2vWjCqgDAegD4AXoAwXoA68C6APhBfUDAAAABA&num=3&sig=AGiWqtzcysI5tCeZiqxQOBdGBhF_4dJbNw&client=ca-pub-9543332082073187&adurl=http://m1339.ic-live.com/698/%3F39804572%26OVMTC%3Dcontent%26site%3Dwww.wikihow.com%26creative%3D3360845056%26OVKEY%3Dtroubleshooting%2520windows%2520xp")
[COLOR=#000000]In-home & phone support for your PC w/Embarq RescueIT Protection Plan[/COLOR]
[COLOR=#006398][RescueIT.Embarq.com]("http://googleads.g.doubleclick.net/aclk?sa=l&ai=BEIlSrEMaSvaHGJfijATC5KjcBaT24nXo6ODWCcCNtwGAsOoBEAEYASCYv48FKAQ4AFDOn5bPBmDJppeN6KSMGKAB4u-l_gOyAQ93d3cud2lraWhvdy5jb226AQk0Njh4NjBfYXPIAQHaATVodHRwOi8vd3d3Lndpa2lob3cuY29tL0FjY2Vzcy1XaW5kb3dzLUZpbGVzLWluLVVidW50dYACAcgC-LSYB6gDAegD4AXoAwXoA68C6APhBfUDAAAABA&num=1&sig=AGiWqtxigfInBE6lwm9-bGUSPhdFcvLyFg&client=ca-pub-9543332082073187&adurl=http://www.microsoft.com/forefront/en/us/trial-software.aspx")[/COLOR][[COLOR=#006398]**_Virtual Dedicated Server_**[/COLOR]]("http://googleads.g.doubleclick.net/aclk?sa=l&ai=BhcazrEMaSvaHGJfijATC5KjcBbqRmY4BqNH3zQrAjbcBkPGVAxAEGAQgmL-PBSgEOABQjZX8jwdgyaaXjeikjBigAa6H4f4DsgEPd3d3Lndpa2lob3cuY29tugEJNDY4eDYwX2FzyAEB2gE1aHR0cDovL3d3dy53aWtpaG93LmNvbS9BY2Nlc3MtV2luZG93cy1GaWxlcy1pbi1VYnVudHWAAgGoAwHoA-AF6AMF6AOvAugD4QX1AwAAAAQ&num=4&sig=AGiWqtyhzQx0sdFAOtqBG0aLFjvqjWMJHQ&client=ca-pub-9543332082073187&adurl=http://www.opusinteractive.com/managed-hosting/vclustr-virtuals/index.html%3F_kk%3Dlinux%2520virtualization%26_kt%3Dba330358-d7b6-46ac-aa9f-2bf529653a25")
[COLOR=#000000]VDS/VPS Windows or Linux Servers. 24/7 Support. Service Guarantee![/COLOR]
[COLOR=#006398][www.OpusInteractive.com]("http://googleads.g.doubleclick.net/aclk?sa=l&ai=BEIlSrEMaSvaHGJfijATC5KjcBaT24nXo6ODWCcCNtwGAsOoBEAEYASCYv48FKAQ4AFDOn5bPBmDJppeN6KSMGKAB4u-l_gOyAQ93d3cud2lraWhvdy5jb226AQk0Njh4NjBfYXPIAQHaATVodHRwOi8vd3d3Lndpa2lob3cuY29tL0FjY2Vzcy1XaW5kb3dzLUZpbGVzLWluLVVidW50dYACAcgC-LSYB6gDAegD4AXoAwXoA68C6APhBfUDAAAABA&num=1&sig=AGiWqtxigfInBE6lwm9-bGUSPhdFcvLyFg&client=ca-pub-9543332082073187&adurl=http://www.microsoft.com/forefront/en/us/trial-software.aspx")[/COLOR][RIGHT][[IMG]http://pagead2.googlesyndication.com/pagead/abglogo/abg-en-100c-000000.png[/IMG]]("http://services.google.com/feedback/abg?url=http://www.wikihow.com/Access-Windows-Files-in-Ubuntu&hl=en&client=ca-pub-9543332082073187&adU=www.Microsoft.com/Forefront&adT=Windows+Protection&adU=www.jigantic.com&adT=Windows+Terminal+Server&adU=RescueIT.Embarq.com&adT=Troubleshooting+Windows+Xp&adU=www.OpusInteractive.com&adT=Virtual+Dedicated+Server&done=1")[/RIGHT]
  Hide these ads
  
      
  Show Ads  
       **[[edit]("http://www.wikihow.com/index.php?title=Access-Windows-Files-in-Ubuntu&action=edit&section=1")] Steps**

 
[LIST=1]
[*]Install [COLOR=green]**gparted**[/COLOR] ([COLOR=green]**System &#8594; Administration &#8594; Synaptics Package Manager**[/COLOR] &#8594; search for gparted, mark it for installation and, when it installs, run it from [COLOR=green]**System &#8594; Partition Editor**[/COLOR]). Look for an NTFS partition – it is likely to be the one windows is on.
[*]Having located the partition, write down the name – it will look something like [COLOR=green]**/dev/hda2**[/COLOR]. Do this carefully – this is no time for dyslexia. Now check to see if this is the partition by manually mounting it and looking at the files.
[*]Open a terminal ([COLOR=green]**Application &#8594; Accessories &#8594; Terminal**[/COLOR]) and make yourself root by typing [COLOR=green]**sudo -s**[/COLOR] and pressing enter. You will be prompted for the root password and will then become root. Being root assumes that you know what you are doing – you could easily cause disaster if you make a mistake, so concentrate. Carefully type this line at the prompt and press enter
[*]mkdir /mnt/windows
[*]You may replace [COLOR=green]**/mnt/windows**[/COLOR] with [COLOR=green]**/mnt/windrv**[/COLOR] or any other name you prefer. Now, having created the directory that is going to hold your windows files, type the following command carefully at the prompt and press enter
[*]mount -t ntfs /dev/sda2 /mnt/windows -o "umask=022"
[*]Make sure you replace [COLOR=green]**/dev/sda2**[/COLOR] with the name of the windows partition you wrote down. Now access the mounted drive and ensure that you can read the files by going to [COLOR=green]**Places &#8594; Computer**[/COLOR] and navigating to [COLOR=green]**/mnt/windows**[/COLOR]. If you can see your files, you are all set. If not, you've mounted the wrong drive, unmount it using [COLOR=green]**umount /dev/sda2**[/COLOR], making sure that you use the correct name for your drive.
[/LIST]
 

 
     **[[edit]("http://www.wikihow.com/index.php?title=Access-Windows-Files-in-Ubuntu&action=edit&section=2")] Tips**

 
[LIST]
[*]Now, you will probably want to have the computer boot up and automatically mount the windows drive so you can save files back and forth seamlessly. This is easily achieved via a script that loads at startup. The commands in the script will have to be run with root permissions, so you will have to save the file in [COLOR=green]**/etc/init.d**[/COLOR]. You are going to use the same command you used manually. Most of the other lines in the script are comments.
[*]Start a text editor as root by typing [COLOR=green]**gedit /etc/init.d/mountwinfs.sh**[/COLOR]. Copy the lines below into the text editor and save it as [COLOR=green]**/etc/init.d/mountwinfs.sh**[/COLOR].
[*]!/bin/bash
[*]BEGIN INIT INFO
[*]Provides: mountwinfs
[*]Required-Start: $local_fs
[*]Required-Stop:
[*]Default-Start: S
[*]Default-Stop:
[*]Short-Description: Mount the windows file system
[*]Description: Mount the windows file system
[*]END INIT INFO
[*]mount -t ntfs /dev/sda2 /mnt/windows -o “umask=022&#8243;
[*]Do not forget to replace [COLOR=green]**/dev/sda2**[/COLOR] with the name of the windows partition you wrote down. Also, don't forget to replace [COLOR=green]**/mnt/windows**[/COLOR] with whatever you decided to call the directory. Save the file.
[*]The file will be owned by root. You need to set permissions for the file, so it can be executed as follows.
[*]chmod +x mountwinfs.sh
[*]Now you need to convince Ubuntu to run this file at startup. This is done using the command below.
[*]update-rc.d mountwinfs.sh defaults
[*]This command will create links to start the script at runlevels 2, 3, 4, 5 and links to stop it at runlevels 0, 1, 6 (halt, single user and reboot runlevels)
[*]Now to test what you have done...close all windows and restart the computer. Open the file browser ([COLOR=green]**Places &#8594; Computer**[/COLOR]), navigate to [COLOR=green]**/mnt/windows**[/COLOR] and make sure you can see your files.
[*]Your final task is to make a link to [COLOR=green]**/mnt/windows**[/COLOR] on your desktop. Doing this through your file manager is not easy, since you are not root and you only "own" files at your home directory and below. As before, open up your terminal ([COLOR=green]**Application &#8594; Accessories &#8594; Terminal**[/COLOR]) and make yourself root by typing [COLOR=green]**sudo -s**[/COLOR] and pressing enter. You will be prompted for the root password and will then become root. Enter the following command to create the link to your folder.
[*]ln -s /mnt/windows ~/Desktop
[*]You should now have ready access to your windows files every time you log in.
[/LIST]
_______________________________________________________________________________

I do have access to my windows files.  i guess i have to wait til i can afford a external hard drive. cuz i got over a hundred gigs of stuff to back up.  but like i said i can get into windows files.  so in my error i found the ntdll.dll file.  downloaded a new one from [www.dll-files.com](www.dll-files.com).  deleated the old one and installed the new one.  before when i was trying to load windows i would see their welcome screen then it would reset.  i pulled the error and it was that file.  now it just sits on the welcome screen.  so im lost again.  but atleast i got my files.  so if i did a system restore from my windows disk i would lose everything right.  even ubuntu.  i have a 2 gig flash drive.  can i fit just ubuntu on this.  and when i get a external hd i can do the rest.  i think there is a virus in windows.  i dont know how well the ubuntu virus scanner will work.  but now that i have the windows "disk" open in ubuntu i can virus scan windows through ubuntu right.

We do need one clarification - did you actually create a partition for Ubuntu and install it to it, or have you only done the WUBI stuff?

I believe the reason your attempt at replacing the dll didn't work is registry related - date/time etc. stamp probably doesn't match, etc..  Can you press F8 at the very start and get the Windows boot selection screen, and if so, can you boot into safe mode?  If so, assuming you left everything as is, you should be able to try a windows restore (not an installation restore, but rather the restore built in to Windows) and see if that gets Windows back for you.

Dave :)

---

### Post by Leshinsky on 2009-05-25
i can get to that f8 screen but if i choose any other mode, including safe mode, i get a dos looking file system then it just freezes,  if i choose last known config or normally it just freezes when the first windows xp screen comes up (the blue thing that moves from left to right keeps moving but i left it for a hour and it didnt do anything after that.\)  i have access to all my windows files through ubuntu.  and i only installed it as wubu.  or whatever that was.  you know what im saying.  i did not set up a partition.  any ideas to get me back into windows.  if this dont work then i will just use ubuntu and when i get a external hd to back up my information.  another question when we get this one figured out or i just give up.  

i like to chat in [www.talkcity.com](www.talkcity.com)  i can sign in and everything, but when the chat app loads it says need missing plug ins, i install the ones it says i need to and reload the app,  i get the same error message saying the same drivers are missing.  what is going on.  also if i pull up a site like [www.youtube.com](www.youtube.com) the video windows are all grey with a white play button in it.  click on the play button and it says need plugin.  i search for the plug in, does not find one.  my little sister (12 so she dont know nothing,  but likes to think she does so i cant ask her lol) just got a new computer and it only has ubuntu.  she can look at all video.  i spoke with the guy who built her computer and put it on and he told me to go into package mgr, and search for adobe flash.  i did and still cant view videos.  any help on all of this that i am lost to.

---

### Post by Paqman on 2009-05-25
Within Wubi your Windows filesystem is found at /host. So if you can boot into Ubuntu then you can recover your data. Alternatively you can use the Ubuntu LiveCD to boot up into a live sessions of Ubuntu and mount your Windows NTFS partition from there (just go to Places, same as normal)

---

### Post by mangurt on 2009-05-25
Here's a guide if you want to use the ubuntu live cd to back up your data

[http://www.howtogeek.com/howto/windows-vista/use-ubuntu-live-cd-to-backup-files-from-your-dead-windows-computer/](http://www.howtogeek.com/howto/windows-vista/use-ubuntu-live-cd-to-backup-files-from-your-dead-windows-computer/)

As for flash, you can go to the adobe website and install it from there.

---

### Post by Leshinsky on 2009-05-25
ok,  my last post had a problem with java and flash as well. any takers on those problems in ubuntu.  noone seemed to touch it.

---

### Post by mangurt on 2009-05-25
Here's a pretty good guide to install java and flash.

[http://ubuntuforums.org/showthread.php?t=766683&highlight=install+java](http://ubuntuforums.org/showthread.php?t=766683&highlight=install+java)

---

### Post by Leshinsky on 2009-05-25
ok, i tried that last post.  tried everything.  got no errors.  still can not run java based web apps.  also when i use a web based image host i can see the list and preview thumbnails, but when i try to view a gallery it shows the block the picture is normally in but no picture.  

when i attempt to watch videos on youtube i am now told to install missing plugins.  when i do this it tells me that the requested plugins were installed but did not provide all requested plugins.  any help.

The next post is what i did.  the one after it is a cut and paste from my terminal window.

---

### Post by Leshinsky on 2009-05-25
Well now it wont let me cut and paste so i dont know.i will leave the terminal window open incase anyone has any ideas.

---

### Post by lisati on 2009-05-25
> **Leshinsky said:**
> 
STOP: c0000221 unknown hard error
\systemroot\system32.dll

This is a Windows error.

I've had a quick look at the previous posts. This is my $0.02:
You might need to use a LiveCD to boot your system and copy your important files to CD/DVD or an external hard drive, then reinstall Windows and/or Ubuntu. Chances are that because Windows is having problems, Ubuntu will complain about "unclean" volume (or some such error), but there are ways to cope; I'm sure someone will be able to offer suggestions if that comes up.

---

### Post by rob2uk on 2009-05-25
> **Leshinsky said:**
> STOP: c0000221 unknown hard error
\systemroot\system32.dll

system32.dll is NOT a Windows file, it's the Harnig trojan...

Time to crack out the AV - your Windows install may or may not be recoverable :(

---

### Post by Leshinsky on 2009-05-26
Ok,  well i still am having the same problems with ubuntu.  How do i wipe the drive and just put on ubuntu.  Also i have a older internal (desktop computer) hard disk.  i dont know it may or may not work still.  i read somewhere i can get a "stand" for it, plug the hard drive into the "stand" and then plug the "stand" into my usb.  it only costs 30 bucks.  roughly.  anyone try this with ubuntu.  it would be worth the money seeing how it is a 400 gb hd.  let me know.

---

### Post by Leshinsky on 2009-05-26
also it was not a system32.dll file it was a ntdll.dll.  but i will look for system32.dll just incase.  where would that normally be hiding.

---

### Post by mangurt on 2009-05-26
To install Ubuntu, put in the live cd and do the complete install.  There is a post in this tread for mounting your windows hard drive to retrieve your information of of your windows drive.

The other about multimedia installation is once ubuntu is installed on your system.

---

### Post by Leshinsky on 2009-05-26
ok, my computer does not have any cd r dvd or anything drives. it has usb. so i was thinking use a flash drive to do it.  (flash drives are bootable on this system). then i would just download the ubuntu from the site and put it on a flash drive.  can this be done. and does anyone know anything about mounting that old internal hd as a external.  like i mentioned before.

---

### Post by rob2uk on 2009-05-26
> **Leshinsky said:**
> does anyone know anything about mounting that old internal hd as a external.  like i mentioned before.

Easy, pick up an [external HDD enclosure ]("http://www.pcworld.co.uk/martprd/store/pcw_page.jsp?BV_SessionID=@@@@1976540103.1243353605@@@@&BV_EngineID=ccehadehgegdhffcflgceggdhhmdgmk.0&page=Product&sku=492710&category_oid=null&fm=undefined&sm=undefined&tm=undefined"), take the drive out of the PC and connect the cables in the enclosure to it.

Plug it into a spare USB port and you're away

---

### Post by Leshinsky on 2009-05-26
where is a good place to pick one up.

---

### Post by mangurt on 2009-05-26
> **Leshinsky said:**
> ok, my computer does not have any cd r dvd or anything drives. it has usb. so i was thinking use a flash drive to do it.  (flash drives are bootable on this system). then i would just download the ubuntu from the site and put it on a flash drive.  can this be done. and does anyone know anything about mounting that old internal hd as a external.  like i mentioned before.
Here's the instructions on creating a boot usb in windows

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by grungedoobie on 2009-05-26
> **Leshinsky said:**
> Ok,  here is what i have.  I am using a dual boot from wubi-installer.  I have Ubuntu (i believe on a partition) and windows xp.  i have been using ubuntu and like it so far.  so i am trying to get some pictures from xp, and of course i got a virus on it.  when i boot up i get this error:
STOP: c0000221 unknown hard error
\systemroot\system32.dll

I looked all through windows forums and the only way they say to fix this is to be in windows. (or a hardware problem which it could be a driver in windows, but not hardware is messed up cuz it all works in ubuntu, which i am using now on the same computer).  so my question is does anyone know a way to fix this from ubuntu, (registary error) or is there a way i can pull my files over without getting into windows (through ubuntu) since i want to get rid of windows anyways.

***  WARNING  ***

!!!Backups Backups Backups!!!  Do not continue reading this post until you make a full backup of your stuff to another device or at least another partition.



Your original post says that Windows has messed up its system files and is in the process of crashing.  Use the Windows install disk to repair your system so that you can boot it up.  Run a virus scanner!  Then run every update your Windows updater can find.  (Updating windows XP from SP1 and SP2 disks will take a long time so make a full pot of coffee.)  Clean your Windows machine up!  Remove trash files.  Remove registry errors if possible.  Remove software that you never use from the add remove section.  Scan the hard drive for errors.  Lastly, defrag the drive.  If you have a bunch of support stuff running in the background like toolbar helpers and such, turn those off while running maintenance else they will add blight to your failing OS and give you finger cramps.  :confused:

Using Wubi... If your Windows is crashing, it will take Wubi with it if you don't fix Windows pretty quick.

Windows has been and always will be a dirty running high maintenance operating system which will destroy itself if you don't learn how to keep it tidy.  People who are happy with what they have don't go out and buy the next one.  Microsoft knows this and shoves it on their paytrons.  (My bad for strong words.)

Is there a way you can get hands on another hard drive.  Do the real install of Ubuntu 9.04 Jaunty?  Mess with just Ubuntu for a bit and decide which ones best for you.

With Jaunty, I've had no problems with most websites.  I'm even able to run Yahoo's junk with all their advertising and Micro-Only attitude beautifully with Jaunty.

Have you added Medibuntu to your package lists?


The Grunge

---

### Post by rob2uk on 2009-05-26
> **Leshinsky said:**
> where is a good place to pick one up.

[Clicky]("http://maps.google.co.uk/maps?oe=utf-8&rls=com.ubuntu:en-GB:unofficial&client=firefox-a&um=1&ie=UTF-8&q=salt+lake+city+computer+stores&fb=1&split=1&gl=uk&view=text&ei=KSkcSpP-HuLTjAfcnPXsDA&sa=X&oi=local_group&ct=more-results&cd=1&resnum=1") :)

---

### Post by grungedoobie on 2009-05-26
> **Leshinsky said:**
> Ok,  well i still am having the same problems with ubuntu.  How do i wipe the drive and just put on ubuntu.  Also i have a older internal (desktop computer) hard disk.  i dont know it may or may not work still.  i read somewhere i can get a "stand" for it, plug the hard drive into the "stand" and then plug the "stand" into my usb.  it only costs 30 bucks.  roughly.  anyone try this with ubuntu.  it would be worth the money seeing how it is a 400 gb hd.  let me know.

My bad, didn't catch the post about not having a writable optical drive.  

As far as the external drive goes, I use USB converters for drives without any hangups.

On my part though, I ripped open a USB drive case to get my IDE/USB converter.  It works flawlessly on all IDE drives and have even used it to stress test drives and burn cd's.  You'll probably need to search around and match a converter to your drive type.  There are also all-in-one USB/IDE/SATA converters out there to look at.  Google is your friend.

I have made bootable USB Hard drives, but they can be very ticky as the data flow through USB is not as fast or strong as through IDE or SATA.

Even a monster box with a kicking OS will lag when channeled through USB.

Luck to you,


The Grunge.

---

### Post by rob2uk on 2009-05-26
The USB enclosure I have cost me £12 (less than $20 US), has both SATA and IDE connectors, has survived just about everything except nuclear war, and still runs perfectly.

---

### Post by Leshinsky on 2009-05-26
well i took a cross country trip with that drive with it in a paper bag.  (the drive not the computer) i am a bit worried it might not work.  but even if i get the connector and the drive dont work i can still get a new internal drive and connect it to the connector.  since internal are a lot cheaper than external.  what size would i need.  it is a four year old gate way desktop hard disk.  i think the connectors are the same still as they were 15 years ago.  i just dont know the size.

---

### Post by rob2uk on 2009-05-26
IDE by the sounds of it.

If you get an enclosure with both IDE  and SATA it doesn't matter if your old drive doesn't work - SATA is identical on 2.5" and 3.5" drives, but you get more for your money on the 3.5" ones

---

### Post by Leshinsky on 2009-05-26
it says maxtor 3.5 series.  so i assume that means 3.5

---

### Post by rob2uk on 2009-05-26
yup :)

Desktop drives are 3.5", laptop ones are 2.5"

---

### Post by Leshinsky on 2009-05-26
so after this i can totally get rid of windows.  i might need some help as that other drive has windows xp on it as well.  it was from my old computer when i moved i figured it was way to old to bring with me to i ganked the drive out and brought it with me.

---

### Post by rob2uk on 2009-05-26
the XP install is probably useless to be honest - It probably won't boot on your new machine.

Any files you have on there can probably be rescued as long as the drive's not physically damaged though

---

### Post by Leshinsky on 2009-05-26
what i was thinking is hook it up.  bring all the files off of there i may want.  wipe that drive totally.  then put all the files i took off of there and put the ones i want to keep on this one on there.  disconnect it and use a usb flash drive to put ubuntu on this.  how would i wipe this drive.  and is there a site i can download ubuntu.  and that way this compuer will only have ubuntu right.  also i am looking at getting a new compuer very soon.  like a few weeks.  and getting a new desktop both of which will run ubuntu.  if i do this i would make the one i have now a server.  basically for files.  i have a cat 5 line running in for internet which will go into a wired/wireless router.  so that will share the internet.  would it be better to just reload ubuntu server on this computer or just plain old ubuntu.  it will act as a server for files and printers.  scanners cams etc.

---

### Post by Leshinsky on 2009-05-26
this way the new computers wont have anything but the os on them.  but i would like more of a real network set up where i can handle login information from the server and all that.

---

### Post by rob2uk on 2009-05-26
you're probably better off leaving the server thing until you're a bit more confident, in my opinion.

Ubuntu can be downloaded from [here]("http://www.ubuntu.com/") - it's a CD image, so you'd need to burn it and boot from the disk.

The installer will guide you through repartitioning your hard disk, but you will need to make a backup of everything important first

---

