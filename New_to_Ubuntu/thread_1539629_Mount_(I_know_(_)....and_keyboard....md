---
title: "Mount (I know :( )....and keyboard..."
date: 2010-07-26
forum: New to Ubuntu
---

### Post by Gregor Samsa13 on 2010-07-26
Hey first of all I want to make apoligize for my English and hope that will be good enough.
So, my big problem is mounting media in my DVD player...I tried many commands known in terminal (now I can not remember which) but all which I have found on net...

like this: mount -t iso9660 -o ro /dev/cdrom /cdrom but then say **only root can do that**

With command: cat /etc/fstab

I get this:
/etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=380523df-11b1-45dd-aaae-67c0a6998a10 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=1afd4f70-ac2a-437e-b04b-9bbdb253fd6e none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

Another problem is keyboard...I m from Serbia and I allready install serbian lng but after reboot it always disappear...

So if somebody know to solve this I bee very grateful.
Tnx!

---

### Post by MooPi on 2010-07-26
Add before your command ```
sudo
```
The DVD or CD should be auto mounting, maybe your drive is not functioning properly?

---

### Post by Gregor Samsa13 on 2010-07-26
> **MooPi said:**
> Add before your command ```
sudo
```
The DVD or CD should be auto mounting, maybe your drive is not functioning properly?

It does...I have xp on second boot...
for some reason now it working...but this is second time today that he is mounting DVD and then not...

---

### Post by jtarin on 2010-07-26
> Another problem is keyboard...I m from Serbia and I allready install serbian lng but after reboot it always disappear...

So if somebody know to solve this I bee very grateful.
Tnx!

Go to System > Administration > Language Support. You shouldn't need to install the Serbian language packs but click on the Install/Remove Languages button anyway, highlight Serbian and tick the Translations and Spellchecking and writing aids boxes and click apply to make sure you've got everything you need. To change settings to Serbian, I had to go to the 'Text' tab and change that before I could select Serbian in the Language tab.

---

### Post by Gregor Samsa13 on 2010-07-26
> **jtarin said:**
> Go to System > Administration > Language Support. You shouldn't need to install the Serbian language packs but click on the Install/Remove Languages button anyway, highlight Serbian and tick the Translations and Spellchecking and writing aids boxes and click apply to make sure you've got everything you need. To change settings to Serbian, I had to go to the 'Text' tab and change that before I could select Serbian in the Language tab.

Done that long before but it didnt help to keyboard to type on serbian if I dont after reboot do:

setxkbmap -layout rs,rs -variant latin, -option compose:rwin,lv3:ralt_switch,grp:alt_shift_toggle

...but I dont think is solution to do always that after I reboot machine...:/

---

### Post by jtarin on 2010-07-26
> **Gregor Samsa13 said:**
> Done that long before but it didnt help to keyboard to type on serbian if I dont after reboot do:

setxkbmap -layout rs,rs -variant latin, -option compose:rwin,lv3:ralt_switch,grp:alt_shift_toggle

...but I dont think is solution to do always that after I reboot machine...:/Try adding that command to your /etc/rc.local file to run at boot.I always do this in my Slackware install to start anything I want before the GUI comes up.

---

### Post by Gregor Samsa13 on 2010-07-27
> **jtarin said:**
> Try adding that command to your /etc/rc.local file to run at boot.I always do this in my Slackware install to start anything I want before the GUI comes up.

I did that with no success (If I done right what you wrote me, in terminal I wrote that command and then setxkbmap -layout rs,rs -variant latin, -option compose:rwin,lv3:ralt_switch,grp:alt_shift_toggle ?)

Like this again mount is not working and after I wrote a command>

 sudo mount -t iso9660 -o ro /dev/cdrom /cdrom

I got answer:

mount: /dev/sr0 already mounted or /cdrom busy
mount: according to mtab, /dev/sr0 is already mounted on /cdrom

---

### Post by jtarin on 2010-07-27
> **Gregor Samsa13 said:**
> I did that with no success (If I done right what you wrote me, in terminal I wrote that command and then setxkbmap -layout rs,rs -variant latin, -option compose:rwin,lv3:ralt_switch,grp:alt_shift_toggle ?)

Like this again mount is not working and after I wrote a command>

 sudo mount -t iso9660 -o ro /dev/cdrom /cdrom

I got answer:

mount: /dev/sr0 already mounted or /cdrom busy
mount: according to mtab, /dev/sr0 is already mounted on /cdromI'm only addressing your Serbian language problem with your keyboard...._not your mount problem at this time_. One problem at a time please.
In the terminal type "sudo gedit" as root...enter your password... and with gedit (not the terminal) make your way to the file /etc/rc.local
When it is open add your command as the last line....save and exit. Reboot and tell me the results.

Why are you trying to mount your CD? It should automount when you have inserted a disk in the player.
Try the command 
```
sudo start autofs
```
to see if it will mount when you insert a CD.

---

### Post by Gregor Samsa13 on 2010-07-27
> **jtarin said:**
>  /etc/rc.local
When it is open add your command as the last line....save and exit. Reboot and tell me the results.

Ok, but I dont have /etc/rc.local i have numerous rc0.d, rc1.d....rc6.d, and rcS.d ?

I didnt see about mount...well it never do automatic mount...two times after many commands with no reason start to automount but also like keyboard after reboot it want mount any media...

I m sorry I fell like idiot with all this...and must go so I will not be at home...

---

### Post by akoskm on 2010-07-27
> **Gregor Samsa13 said:**
> Ok, but I dont have /etc/rc.local i have numerous rc0.d, rc1.d....rc6.d, and rcS.d ?

Have you tried just adding the kbd layout switcher applet to your panel?
If not, then go to System > Preferences > Keyboard > Layouts tab, add the Serbian language.
After Applying the settings the language switcher applet comes up on your Panel.
Hope that helps.

---

### Post by Gregor Samsa13 on 2010-07-27
> **akoskm said:**
> Have you tried just adding the kbd layout switcher applet to your panel?
If not, then go to System > Preferences > Keyboard > Layouts tab, add the Serbian language.
After Applying the settings the language switcher applet comes up on your Panel.
Hope that helps.

Yes, that was my nature way because I change often lng...but that did not do anything...after reboot it doesent recognize any other lng beside english.

---

### Post by akoskm on 2010-07-27
> **Gregor Samsa13 said:**
> Yes, that was my nature way because I change often lng...but that did not do anything...after reboot it doesent recognize any other lng beside english.

What do you mean by doesn't recognize?
The Language Switcher applet doesn't show up, and/or after reboot the system resets your setting configured in Keyboard Layouts?
Here is my configuration:
[http://imagebin.org/106943]("http://imagebin.org/106943").

---

### Post by jtarin on 2010-07-27
> **Gregor Samsa13 said:**
> Ok, but I dont have /etc/rc.local i have numerous rc0.d, rc1.d....rc6.d, and rcS.d ?


/etc/rc.local is a editable text file not a directory. You need to go further down into your /etc directory to see the text files.
Try the command in your terminal
```
sudo gedit /etc/rc.local
```

---

### Post by Gregor Samsa13 on 2010-07-29
> **jtarin said:**
> /etc/rc.local is a editable text file not a directory. You need to go further down into your /etc directory to see the text files.
Try the command in your terminal
```
sudo gedit /etc/rc.local
```

I open it and then I have this picture...

[http://img148.imageshack.us/img148/4272/201007291117551280x1024.png](http://img148.imageshack.us/img148/4272/201007291117551280x1024.png)

I put at the end but nothing....


> **akoskm said:**
> What do you mean by doesn't recognize?
The Language Switcher applet doesn't show up, and/or after reboot the system resets your setting configured in Keyboard Layouts?
Here is my configuration:
[http://imagebin.org/106943]("http://imagebin.org/106943").

I dont have that way switcher neither a option like you do here in Lubuntu...


 * Ok I hope after this it gonna work longer then one reboot...with lnk keyboard I than this:

**sudo leafpad /etc/xdg/lxsession/Lubuntu/autostart**

and add in my case serbian layout with this

**@setxkbmap -layout rs,rs -variant latin, -option compose:rwin,lv3:ralt_switch,grp:alt_shift_toggle**

Now mount of media only left...

---

### Post by Gregor Samsa13 on 2010-07-29
Ok I think I fixed my problem with mounting and it was a floopy in BIOS (which is now turn off) which made a chaos of all thing...
Thanx for all people for a good will who make posts about my problem.

---

### Post by jtarin on 2010-07-29
> **Gregor Samsa13 said:**
> I open it and then I have this picture...

[http://img148.imageshack.us/img148/4272/201007291117551280x1024.png](http://img148.imageshack.us/img148/4272/201007291117551280x1024.png)

I put at the end but nothing....

Did you sudo before the command?

You need to change permissions on the file....it shows read only. Right click and choose properties and give it read, write and make executable permission and save.Then edit it.

---

