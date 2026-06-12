---
title: "VGA=786 is deprreciated error"
date: 2011-04-23
forum: New to Ubuntu
---

### Post by razedafear on 2011-04-23
Hi , I am a newbie to ubuntu.. i changed some setings in startup manager trying to change the logon n login screen and the themes. but when i start the ubuntu from bootup it gives me this error 
"VGA=786 id deprreciated error " ............................Use set gfxpayload....


i dont know hoe to edit grub and other system files....can somebody help ..
Thanks

---

### Post by oldfred on 2011-04-23
Is yours an upgrade from grub legacy that had a vga parameter. That often gets copied over incorrectly.

vga=xxx is a deprecated boot option
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/454993](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/454993)
"VGA Deprecated" Message on Boot
[http://ubuntuforums.org/showthread.php?t=1453524](http://ubuntuforums.org/showthread.php?t=1453524)

Do you get the grub menu? You can edit the line for one time to boot using e and remove the parameter.

Then to fix 

gksudo gedit /etc/default/grub
sudo update-grub

---

### Post by razedafear on 2011-04-25
Hi oldfred

Thanks for the prompt reply. But i am absolutly new to the linux environment. (sounds a bit lame!)
here are couple of things 

# "Is yours an upgrade from grub legacy that had a vga parameter" - dont know wht dis means

# Do you get the grub menu? - Yes i do get the grub menu.

#  You can edit the line for one time to boot using e and remove the parameter. - i press e and i can edit the commands, which parameter is to be removed. What all commands do i have to run at grub prompt i mean @ "grub>".

Thanks again for being helpful but if its possible for you to explain in a step by step manner it would be helpful... I am eager to learn linux. I dont knw why i was stuck with a crap called windows...

---

### Post by oldfred on 2011-04-25
If you get the grub2 menu, you just press e for edit and scroll to the line with the VGA= and edit it out. Then control X boots with that edit. It is a one time change.

If you are just getting to a grub prompt you are not booting and need to reinstall grub2 to the MBR.

Please post this:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by JKyleOKC on 2011-04-25
> **razedafear said:**
> i changed some setings in startup manager trying to change the logon n login screen and the themes. but when i start the ubuntu from bootup it gives me this error 
"VGA=786 id deprreciated error " ............................Use set gfxpayload....There's a bug in the startup manager in that it writes the VGA= option to grub's configuration file although at least the last two versions of Ubuntu have not used it and instead give that message (which is really a warning rather than an error).

You can get rid of it in either of two ways. One is to remove it from grub's configuration file, and the other is to force the kernel to use the older video code that does recognize it. I've done it both ways on my machines and find no difference between them.

To remove it from the configuration file, first get into a terminal window and from there enter the command "gksudo gedit /etc/default/grub" to open the file for editing. you'll see two lines that start like this```
GRUB_CMDLINE_LINUX_DEFAULT=""
GRUB_CMDLINE_LINUX=""

```but they will have words inside of the quotes; I've removed all the options from my copy. Some of those words will be the VGA= string; delete it and then save the file and exit.

Next, run the command "sudo update-grub" and type your password when requested. Nothing will echo to the screen but it IS going in. When you get the prompt back, type "exit" and you're done.

To force the kernel to use the older mode, do the same things up to deleting the VGA= string, but leave the string in place. Just before the closing quote of both lines, add " nomodeset" (without additional quotes but with the leading space), then save, exit, and run update-grub.

Hope this helps!

---

### Post by razedafear on 2011-04-26
> **JKyleOKC said:**
> There's a bug in the startup manager in that it writes the VGA= option to grub's configuration file although at least the last two versions of Ubuntu have not used it and instead give that message (which is really a warning rather than an error).

You can get rid of it in either of two ways. One is to remove it from grub's configuration file, and the other is to force the kernel to use the older video code that does recognize it. I've done it both ways on my machines and find no difference between them.

To remove it from the configuration file, first get into a terminal window and from there enter the command "gksudo gedit /etc/default/grub" to open the file for editing. you'll see two lines that start like this```
GRUB_CMDLINE_LINUX_DEFAULT=""
GRUB_CMDLINE_LINUX=""

```but they will have words inside of the quotes; I've removed all the options from my copy. Some of those words will be the VGA= string; delete it and then save the file and exit.

Next, run the command "sudo update-grub" and type your password when requested. Nothing will echo to the screen but it IS going in. When you get the prompt back, type "exit" and you're done.

To force the kernel to use the older mode, do the same things up to deleting the VGA= string, but leave the string in place. Just before the closing quote of both lines, add " nomodeset" (without additional quotes but with the leading space), then save, exit, and run update-grub.

Hope this helps!

==========================

Well this looked pretty helpful but i get stuck at a point where i have to type "gksudo gedit /etc/default/grub". I am typing it in grub prompt ( grub> )that i get when i press edit.
I think if I can find a video tutorial on this that will be helpful. Or may be if someone can make a tutorial on this specific error.
I am pissed off by this error... 

:confused:

---

### Post by oldfred on 2011-04-26
If you are just getting a grub prompt, you have not booted at all. The command is to be run from a terminal mode after booting.

Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)

You can try manual booting.

Adjust drive, partition to your install example is hd1,1 or sdb1:
sh:grub>ls
#If on (hd1,1) or sdb1
sh:grub>ls (hd1,1)/
#Should show the links vmlinuz & initrd.img
sh:grub>linux (hd1,1)/vmlinuz root=/dev/sdb1
sh:grub>initrd (hd1,1)/initrd.img
sh:grub>boot

---

