---
title: "Touch pad not working"
date: 2011-04-26
forum: New to Ubuntu
---

### Post by Ymurti on 2011-04-26
I have a lap top Sony Vaio with Windows 7 and Ubuntu 10.04 LTS
The touch pad works in Windows but not in Ubuntu.

I typed:   xinput --list      in a terminal window and here it is the result:

&#9121; Virtual core pointer                    	id=2	[master pointer  (3)] 
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)] 
&#9116;   &#8627; Logitech USB Receiver                   	id=10	[slave  pointer  (2)] 
&#9116;   &#8627; Logitech USB Receiver                   	id=11	[slave  pointer  (2)] 
&#9116;   &#8627; Macintosh mouse button emulation        	id=13	[slave  pointer  (2)] 
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)] 
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)] 
    &#8627; Sony Vaio Keys                          	id=6	[slave  keyboard (3)] 
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)] 
    &#8627; Power Button                            	id=8	[slave  keyboard (3)] 
    &#8627; USB 2.0 Camera                          	id=9	[slave  keyboard (3)] 
    &#8627; AT Translated Set 2 keyboard            	id=12	[slave  keyboard (3)] 

Please can someone help me?

---

### Post by mattbutsko on 2011-04-26
Here's a fix posted by terry.r:

> Here's the fix:

1. Edit /etc/default/grub to include GRUB_CMDLINE_LINUX="i8042.nopnp"
2. Run: sudo update-grub
3. Reboot.

I used to have to do this with a new install til I upgraded to 10.10, but I can confirm this works on my Vaio F with 10.04.

---

### Post by matt_symes on 2011-04-26
Hi

Your touchpad is recognised and that is good. Let's make sure it's not disabled in Gnome.

Open a terminal and copy and paste ...

```
gconftool-2 --set --type boolean /desktop/gnome/peripherals/touchpad/touchpad_enabled true

```
Kind regards

---

### Post by Ymurti on 2011-04-26
> **mattbutsko said:**
> Here's a fix posted by terry.r:



I used to have to do this with a new install til I upgraded to 10.10, but I can confirm this works on my Vaio F with 10.04.
Dear mattbutsko,

I tried the first command:
 
/etc/default/grub to include GRUB_CMDLINE_LINUX="i8042.nopnp"

and got this:

Permission denied

---

### Post by Ymurti on 2011-04-26
> **matt_symes said:**
> Hi

Your touchpad is recognised and that is good. Let's make sure it's not disabled in Gnome.

Open a terminal and copy and paste ...

```
gconftool-2 --set --type boolean /desktop/gnome/peripherals/touchpad/touchpad_enabled true

```
Kind regards
Dear matt_symes,

I tried it but the touch pad still does not work!

---

### Post by mattbutsko on 2011-04-26
Hey man, the first thing isn't really a command.

/etc/default/ is a location and there's a file called "grub" in that folder.

Hit Alt-F2, then type "gksudo nautilus /etc/default/"

Type your password.

Then look for the file "grub" and double click it, should open the file in gedit. Look for GRUB_CMDLINE_LINUX="" and add i8042.nopnp inbetween those quotes. Save the file, the exit out of gedit.

Then, run the command sudo update-grub in the terminal, type your password if it asks for it.

Then reboot the PC via sudo reboot, or do it through your normal fasion.

After you reboot, it should work. I did this two seperate times on 10.04 and I can confirm it worked on my Vaio.

---

### Post by matt_symes on 2011-04-26
Hi

> Dear mattbutsko,

I tried the first command:

/etc/default/grub to include GRUB_CMDLINE_LINUX="i8042.nopnp"

and got this:

Permission denied

Open a terminal and type

```
sudo nano /etc/default/grub
```

Enter your password. It will not be echoed to the screen

Edit the line to be

```
GRUB_CMDLINE_LINUX="i8042.nopnp"
```

Then type 

```
sudo update-grub
```

Reboot

That is what mattbutsko is suggesting.

Kind regards

---

### Post by Ymurti on 2011-04-26
> **mattbutsko said:**
> Hey man, the first thing isn't really a command.

/etc/default/ is a location and there's a file called "grub" in that folder.

Hit Alt-F2, then type "gksudo nautilus /etc/default/"

Type your password.

Then look for the file "grub" and double click it, should open the file in gedit. Look for GRUB_CMDLINE_LINUX="" and add i8042.nopnp inbetween those quotes. Save the file, the exit out of gedit.

Then, run the command sudo update-grub in the terminal, type your password if it asks for it.

Then reboot the PC via sudo reboot, or do it through your normal fasion.

After you reboot, it should work. I did this two seperate times on 10.04 and I can confirm it worked on my Vaio.
Thank You a lot mattbutsko,

It is working my Touch Pad again.

---

### Post by matt_symes on 2011-04-26
Hi

@mattbutsko

i8042.nopnp :) Thanks. I did not know about that.

Kind regards

---

### Post by Ymurti on 2011-04-26
> **matt_symes said:**
> Hi



Open a terminal and type

```
sudo nano /etc/default/grub
```

Enter your password. It will not be echoed to the screen

Edit the line to be

```
GRUB_CMDLINE_LINUX="i8042.nopnp"
```

Then type 

```
sudo update-grub
```

Reboot

That is what mattbutsko is suggesting.

Kind regards
Thank You matt_symes for your reply to my post.

---

### Post by helpneeded2011 on 2011-10-16
Sorry to revive an old thread, but...  > **mattbutsko said:**
> Hey man, the first thing isn't really a command.

/etc/default/ is a location and there's a file called &quot;grub&quot; in that folder.

Hit Alt-F2, then type &quot;gksudo nautilus /etc/default/&quot;

Type your password.

Then look for the file &quot;grub&quot; and double click it, should open the file in gedit. Look for GRUB_CMDLINE_LINUX=&quot;&quot; and add i8042.nopnp inbetween those quotes. Save the file, the exit out of gedit.

Then, run the command sudo update-grub in the terminal, type your password if it asks for it.

Then reboot the PC via sudo reboot, or do it through your normal fasion.

After you reboot, it should work. I did this two seperate times on 10.04 and I can confirm it worked on my Vaio.

I tried this in the hope of bringing back the function of my touch pad.   But now I can't even log in, and I'm faced with a black screen with Glib-WARNING **: getpwuid_r(): failed due to unknown user id (0).     
 
edit: I have found this post, and gone through the link, but as a complete novice of ubuntu, I don't know the first thing I'm doing. [http://ubuntuforums.org/showpost.php?p=9054031&postcount=2](http://ubuntuforums.org/showpost.php?p=9054031&postcount=2)   
 
I am currently posting this on another PC, but please help and assistance is urgently requested! Thanks in advance.

---

### Post by helpneeded2011 on 2011-10-16
^ If anyone can help...  It would be much appreciated.

---

