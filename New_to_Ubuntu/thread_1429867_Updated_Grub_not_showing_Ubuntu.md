---
title: "Updated Grub not showing Ubuntu"
date: 2010-03-14
forum: New to Ubuntu
---

### Post by vincentertainment on 2010-03-14
Grub was updated. system was rebooted.
I used to see choices of Windows xp, Ubuntu, and memory test.
Now, only Windows and memory tests show up as options.
I have entered 'C' to get to command-line.

What can I enter to get my ubuntu option back?

PS: I don't have access to a terminal yet. I'm in Grub's command-line.
sh:grub>

---

### Post by Paqman on 2010-03-14
Hmm. What you need to do is get into your Ubuntu system and try to update Grub. The trouble is that you can't boot it at the moment.

What you can do is boot up your LiveCD and use that to access your installed copy of Ubuntu, but it does involve a bit of futzing around with the command line i'm afraid.

[LIST=1]
[*]Boot up into your LiveCD
[*]Follow the instructions [here]("http://ubuntuforums.org/showthread.php?t=1156240") to "chroot" into your Ubuntu install. Preface all those commands with sudo.
[*]At the "do what you have to do" step, execute the following command:
```
sudo update-grub
```
[*]Post the output of that command and let us know if you can now boot Ubuntu.
[/LIST]

---

### Post by 2hot6ft2 on 2010-03-14
Considering this thread is tagged with "dual-boot xp **hardy, grub 1.97~beta4"**.
What version of ubuntu are you referring to?
I mean did you Upgrade grub to Grub 2 on Hardy?

---

### Post by vincentertainment on 2010-03-16
Hardy was a fresh install, rather than an upgrade and its the standard gnome version.
 
I tried the code in the above example and got error messages. I apologize for not posting the errors here but I'm on a different computer at the moment.
 
Is there a grub2 command I can use to update grub or to add my Ubuntu partition?
Thanks

---

### Post by lidex on 2010-03-16
So let me get this right. You had a working dual-boot setup with ubuntu and windows and the only thing you did was upgrade from legacy grub to grub2, is that correct?

---

### Post by julio.tomaschitz on 2010-03-16
well, there is thousands of articles about recovering grub, and grub2.
I prefer the old grub to do this.
booting up the live-cd, you open a terminal, and first step you'll have to mount the ubuntu partition, just clicking on it on 'places'. come back to terminal, type 
sudo chroot /media/ubuntu_partition
now you are root on you ubuntu partition. install the old grub, typing:
sudo apt-get update && sudo apt-get install grub-pc
now the system will try to remove the grub2 and sucessuly install grub"1".
whem finished, lets configure the grub, use the command:
grub
now open other terminal and type:
sudo cfdisk
now remember the number of the partition of the ubuntu instalation (like sda5).
on the 'grub terminal' type:
root (hd0,6)
where 6 is the 5 from sda5 plus 1 (always 1).
if no errors appears, lets install it on MBR, type:
setup (hd0)
and now you can quit with command:
quit

restart the system and see the ubuntu, windows, and memtest on menu.

---

### Post by lidex on 2010-03-16
> sudo apt-get update && sudo apt-get install grub-pc

Unfortunately that command installs grub2. Legacy grub is denoted as simply "grub".

---

### Post by julio.tomaschitz on 2010-03-17
oh, you're right. here is the complete tutorial (it's portuguese, but just follow the commands).
[http://www.vivaolinux.com.br/dica/Removendo-o-Grub2-do-Ubuntu-9.10](http://www.vivaolinux.com.br/dica/Removendo-o-Grub2-do-Ubuntu-9.10)

---

### Post by vincentertainment on 2010-03-17
Thanks for the feedback. I have limited time available to work on this. My last attempt was using Julio's advice. I was successful is loading the live cd and using chroot to get into a terminal as root. 
switching from grub 2 to grub legacy gave me issues, maybe because of the grub**-pc** suffix. 
I'll try it again tomorrow though.
When I pulled up the portuguese tutorial, google offered to translate the page and seems to have done a pretty good job. That method starts off in synaptic. Is using synaptic an option when using a live cd? Can you chroot synaptic too?
Also, grub2 will let me enter command lines at startup. I understand some of the commands and the partition numbers are different in grub2, but would my simplest option be to add my ubuntu partition directly into grub2?

---

### Post by presence1960 on 2010-03-17
why don't we get an exact look at your setup & boot process before making suggestions?

Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

Above link is to meierfra's Sourceforge web page.

This info will give us a clear idea of how to proceed rather than a hunch, guessing or hoping.

---

