---
title: "Near complete install failure"
date: 2010-06-02
forum: New to Ubuntu
---

### Post by RSN CIN on 2010-06-02
Absolute newbie to Ubuntu here.  Got the wife a new HP laptop as an upgrade over our 8-year-old Gateway.  As XP bogged down the Gateway, I decided to check out Ubuntu.  Downloaded the 10.04 LiveCD image, played around with it in wubi, everything worked - wireless, graphics adapter, printer, everything.  Very encouraged by the results, I decided to do a clean install from within wubi.

I should note here that I would have installed from CD boot, but I could not for the life of me get the system to boot from CD.  BIOS was set to look there first.  Even with Ubuntu installed, still cannot get the computer to boot from CD.  This is important later.

Gateway: Pentium 4 1.6ghz, 512mb RAM, 20G HDD, ATI Radeon Mobility M6, PCMCIA wireless card (yes, the box was made before wireless).  As I said, everything worked fine from the LiveCD trial.

Installed from Wubi, and on reboot, I only get a command line.  I am aware of the ATI driver issue, and I tried various commands to reconfigure the driver with no success.

I can start the X system with startx, and various programs like Firefox work, but nothing else.  The CPU is pegged at 100%, I can't use hardware driver preferences (CANNOT ACCESS DBUS or some such) to set up my wireless card, so I can't download any new packages.  I can't mount the CD drive to try to get any files from that.  I can't mount a thumb drive.

Multiple issues, I know.  In order of importance:
1) I would normally try to simply reinstall from CD, but I can't boot from CD.
2) Ubuntu boots to CLI.
3) I can start X with StartX, but no hardware other than the display work.
4) No hardware is configured, despite everything working on the LiveCD.
5) Can't configure wireless or any drive to install/reconfigure packages because of DBUS error.

So so far, my Ubuntu experience has been poor.  I'm approaching a bricked computer, even though it could run XP acceptably.  Where do I start?

---

### Post by Jakiejake on 2010-06-02
WELCOME TO UBUNTU!
What do you see when you boot?

---

### Post by RSN CIN on 2010-06-02
> **Jakiejake said:**
> WELCOME TO UBUNTU!
What do you see when you boot?

Command line.  Well, first the user/password request from the command line, obviously.  No splash screen, no GUI.

---

### Post by clhsharky on 2010-06-02
RSN CIN

KMS (kernel mode setting) default in Lucid most probable cause with older radeon cards and laptops.

Use UMS (user mode setting)by default in Hardy or Karmic or shut KMS off in Lucid.

In terminal after entering user/password

```
gksudo gedit /etc/default/grub
```
add 
> radeon.modeset=0
to this line
> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
to make this 
> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash radeon.modeset=0"
then save, and
```
sudo update-grub
```

Reboot

Sharky

I would try Karmic "Ubuntu9.10"

---

### Post by RSN CIN on 2010-06-02
> **clhsharky said:**
> RSN CIN

KMS (kernel mode setting) default in Lucid most probable cause with older radeon cards and laptops.

Use UMS (user mode setting)by default in Hardy or Karmic or shut KMS off in Lucid.

In terminal after entering user/password...

Awesome.  I'll try that this afternoon. (Working nights, sleeping days...)

> I would try Karmic "Ubuntu9.10"

For clarification - are you suggesting Karmic as a complete solution, or only if your advice above fails?  The trouble would still remain that I can't currently get anything onto the laptop as I can neither boot from CD nor mount any drives.

---

### Post by clhsharky on 2010-06-02
RSN CIN


> For clarification - are you suggesting Karmic as a complete solution,

Yes, burn you a copy from here
[http://releases.ubuntu.com/karmic/](http://releases.ubuntu.com/karmic/)

Test cd to see if it works, if it does, install.
8.04LTS could also be tested, still way newer than your hardware.

If none of the other cds work, use the Command line instructions I gave you.

One last workaround if still fail, would be to replace
> radeon.modeset=0
with
> pci=noacpi

In the Command line instructions I gave you.
> This disables the use of ACPI routing information during the PCI configuration stages.

These tips have been posted before, search forum if not understood.

Don't forget to save and update as instructed.


Sharky

---

### Post by 3rdalbum on 2010-06-02
DON'T use 'startx' - use:

```
sudo service gdm start
```

---

### Post by RSN CIN on 2010-06-03
> **clhsharky said:**
> RSN CIN

KMS (kernel mode setting) default in Lucid most probable cause with older radeon cards and laptops.

Use UMS (user mode setting)by default in Hardy or Karmic or shut KMS off in Lucid.

In terminal after entering user/password

```
gksudo gedit /etc/default/grub
```

add...

Shoot, I left the paper I wrote the message down on, but this didn't work.  I got an error message, something along the lines of "COULD NOT OPEN DISPLAY."

I can follow up with the actual text tomorrow if necessary.

---

### Post by RSN CIN on 2010-06-03
> **3rdalbum said:**
> DON'T use 'startx' - use:

```
sudo service gdm start
```

Okay, I'll try that later today, thanks!  

Will this allow me to load the hardware preferences/drivers?  Do I assume correctly that 'startx' only loads X and not the other parts of the OS/GUI, while this command loads everything?

---

### Post by RSN CIN on 2010-06-03
Follow up newbie question:

Is there a common keystroke during BIOS/boot that forces the computer to boot from CD?  Like I said before, my BIOS settings have it checking the CD drive first, but the computer never actually boots from CD.

Thanks for all the help everyone.

---

### Post by mastablasta on 2010-06-03
You will have to look for how to do it in your motherboard manual. Some motherboard do have a boot menu key where you can select the boot device without actually going to BIOS.

---

### Post by RSN CIN on 2010-06-04
> **RSN CIN said:**
> Shoot, I left the paper I wrote the message down on, but this didn't work. I got an error message, something along the lines of "COULD NOT OPEN DISPLAY."
 
I can follow up with the actual text tomorrow if necessary.
 
OK, the exact text that appears when I try GKSUDO is:
 
(gksudo 1009:) GTK warning **: Cannot Open Display.
 
--------
 
SUDO SERVICE GDM START
 
starts Ubuntu in low graphics mode, asking me to reconfigure my display.  If I try the option to reconfigure, it continually asks to reconfigure my display - I can't get past that dialog box.  If I try to "run Ubuntu in low-graphics mode for just one session" or "restart X", it says to wait a minute while it loads, but it never loads (no HDD access).  I can click OK there and it dumps me back to CLI.
 
Anyone?!?

---

### Post by llawwehttam on 2010-06-04
Wow, you have a real mess there.

sorry, but its true.

I will try to help as much as I can. Firstly ubuntu 10.04 is giving a lot of people grief. I would try downloading and burning a copy of 9.10 which is very stable for me.

Per your problems booting from cd's are you sure it is enabled in the BIOS and is set before hard drives?

I have done this before and issed it.

It is also quite common for F9 to be the boot device select menu in older BIOS's.

Hope some of that helped.

Oh and also if your stuck with CLI```
 gksudo gedit 
```will NOT work as it is a gui program. Instead use```
 sudo vi
``` .  you need to press 'i' for insert mode and then Esc   then :wq when your finished for the save command.

---

### Post by blur xc on 2010-06-04
or sudo nano

As much as I like vim, it's completely anti-intuitive to use.

I still keep a cheat sheet handy when I'm vimming...

BM

---

### Post by bcbc on 2010-06-04
Next time you boot, hold down the shift key, then when the grub menu appears, the first option will be highlighted. Hit the 'e' key to edit it.

Using the arrow keys navigate to the part that says "quiet splash" and you can just add the " radeon.modeset=0" right after that. Then hit CTRL-X to boot.

This way you can figure out if it will solve your problem without editing and regenerating the grub menu each time.

---

### Post by acrazyplayer on 2010-06-04
I hate to sound like im patronizing, but have you burned the cd as an .iso image with a image burner, e.g. brasero "burn image"?

---

### Post by RSN CIN on 2010-06-04
> **llawwehttam said:**
> Wow, you have a real mess there.
 
sorry, but its true.
 
I will try to help as much as I can. Firstly ubuntu 10.04 is giving a lot of people grief. I would try downloading and burning a copy of 9.10 which is very stable for me.
 
Per your problems booting from cd's are you sure it is enabled in the BIOS and is set before hard drives?
 
I have done this before and issed it.
 
It is also quite common for F9 to be the boot device select menu in older BIOS's.
 
Hope some of that helped.
 
Oh and also if your stuck with CLI```
 gksudo gedit 
```will NOT work as it is a gui program. Instead use```
 sudo vi
``` . you need to press 'i' for insert mode and then Esc then :wq when your finished for the save command.
 
This was helpful. I was able to put the "modeset=0" argument in, and that changed the splash screen that momentarily appeared to a pretty one instead of a pixelated one. It still dumps me at CLI. The "noacpi" argument didn't affect a change.
 
I noticed this time around in low graphics mode that there is an error regarding a Microsoft Natural Keyboard 4000 that I had connected to the laptop while installing 10.04. Something about installed along unknown axes or something equally mystifying. Do I have another conflict here in addition to the Radeon card?
 
Neither F8 or F9 force a boot from CD.  Old computer makes me sad.
 
Thanks for the help everyone. Keep 'em coming!

---

### Post by RSN CIN on 2010-06-04
> **acrazyplayer said:**
> I hate to sound like im patronizing, but have you burned the cd as an .iso image with a image burner, e.g. brasero "burn image"?
 
Yes, burned the ISO and did the MD5SUM check.

---

### Post by acrazyplayer on 2010-06-05
I just remembered that GRUB can boot to other media. So I think that GRUB would be able to boot your CD but I'm not entirely sure if/how you can do so. Maybe someone else here knows, but if not I'm off searchin...

---

### Post by acrazyplayer on 2010-06-05
After much searching and trial and error I have found something that may help you. You can use grub to boot from .iso images on your hdd. here is the best way I found but I have not tried it. 

[http://ansi.interblc.com/2010/02/06/howto-boot-iso-images-via-grub2-with-ubuntu/](http://ansi.interblc.com/2010/02/06/howto-boot-iso-images-via-grub2-with-ubuntu/)

---

### Post by acrazyplayer on 2010-06-05
I can now CONFIRM this method works.

His instructions are not the best so if you need help I can. You should be able to do all of this via a command line. 

This is by far the best method to use a .iso image I have ever found and actually got to work.

---

### Post by RSN CIN on 2010-06-06
> **acrazyplayer said:**
> I can now CONFIRM this method works.

His instructions are not the best so if you need help I can. You should be able to do all of this via a command line. 

This is by far the best method to use a .iso image I have ever found and actually got to work.

So the idea would be to set this up and boot from a Karmic 9.10 iso image copied to the HDD, install over 10.04, and hope for the best?  Interesting.  I might take you up on that offer of help; the step of copying the image from the CD is not included.

Here's a question: Why is it that the LiveCD of 10.04 worked just fine with my setup (e.g. found all , but then failed miserably on an actual installation?  Seems kind of bad that I would be drawn in by something that appears to work flawlessly and then crashes...

**EDIT**

Wait.  Is there anything executable on a 9.10/10.04 CD that would allow me to install over my current, failed setup -- something that I could start from the CLI?

---

### Post by acrazyplayer on 2010-06-07
I think you would be better off with a clean install to be honest plus I know of no way to do what you asked inside of Ubuntu. 

I just need to ask you a few questions, do you have internet on the computer you want to install ubuntu on? do you have any sort of gui? I remember you said you had firefox running so I assume you do or are you stuck at the command line interface all the time?

edit: nevermind I re-read your first post and notice you can hardly do anything on it. Maybe to get your pc to boot from a cd you could try taking out the hdd and then turn it on with only the cd in. 

does the computer have an ethernet port? because if so then you could try reinstalling gdm or maybe try getting some ati drivers.

edit2: also I noticed you tried pushing buttons to load the cd. Try pushing all of them, start with f1 and constantly keep hitting it right after you power up the computer and keep hitting it up until grub pops up or the option appears to choose what to boot from, if grub comes up then hit control alt delete and try f2 and so on until hopefully one of them works.

---

