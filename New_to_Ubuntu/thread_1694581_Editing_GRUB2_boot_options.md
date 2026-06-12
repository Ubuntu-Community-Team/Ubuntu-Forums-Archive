---
title: "Editing GRUB2 boot options"
date: 2011-02-24
forum: New to Ubuntu
---

### Post by SebSmith on 2011-02-24
How do i edit the names of the options listed? and how do i remove entries? (not kernels as i only have one)

is the +memtest required?
win 7 dual boot came with system partitiion labeled (windows vista(loader)  ). how do i make this option not show up. when i click the windows 7 loader option it goes into windows just fine.

thanks in advance. i am a noob at this still. bear with me.

---

### Post by seawolf167 on 2011-02-24
All the GRUB2 you could ever want:
[URL="http://ubuntuforums.org/showthread.php?t=1195275"]
http://ubuntuforums.org/showthread.php?t=1195275[/URL]

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by danjahner on 2011-02-24
If you just want to remove entries with a gui program, Grub Customizer works well. 

[https://launchpad.net/grub-customizer]("https://launchpad.net/grub-customizer")

```
sudo add-apt-repository ppa:danielrichter2007/grub-customizer
sudo apt-get update
sudo apt-get install grub-customizer
```

---

### Post by NJPinator on 2011-02-25
FULL INSTRUCTIONS
=============================
I have taken the time to write a full tutorial as to how to customise your GRUB 2 entries. Due to GRUB 2 not being updated after Windows 7's release, it detects it as Windows Vista. You can edit your entries by opening the /etc/grub.d/ directory with administrative priveleges, editing a custom file, then updating the GRUB database. Here I explain:

Open /etc/grub.d/ with root access by opening a Terminal (Applications > Accessories > Terminal) and typing
```
sudo nautilus /etc/grub.d/
```
You will be asked for your password, which WON'T be displayed on screen for security reasons. However, press ENTER after typing your password and a File Manager window will open.

Here you should see several files; The one you'll need is "40_custom". Rename it to "06_custom" and open it. Leave the gEdit window open and close the File Manager. If you haven't already, close the Terminal and if asked, click "Close Terminal" to confirm. Open a new Terminal (Applications > Accessories > Terminal) and enter:
```
gedit /boot/grub/grub.cfg
```
This will open your *current* GRUB 2 configuration file in gEdit. Scroll through the file until you come to a paragraph of code that reads:
```
### BEGIN /etc/grub.d/10_linux ###
menuentry [...]
```
This is where the list of your Linux Kernel entries begin. Find the **menuentry 'Ubuntu, with Linux X.X.xx-xx-generic' [...]** that corresponds to your desired GRUB 2 entry. Select the text that is contained between...
```
menuentry 'Ubuntu, [...]

and

initrd [filename]
}
```
...inclusive, and copy it to the clipboard by right-clicking the selected text and clicking "Copy".

Now open the gEdit *tab* 06_custom in the same window and paste the copied text at the *bottom* of the file, without deleting the text already in the file. You can do this by pressing CTRL+END then right-clicking in the text area and clicking "Paste". You can edit the title of the menu entry by replacing the text in quotes (') after **menuentry** with your own. Be sure to keep the desired text in single quotes!

You can now save the **40_custom** file and close its tab by clicking the "X". You should return to the **grub.cfg** tab. DO NOT save this file; this could result in an un-bootable system!!! Simply close the gEdit window and if asked, click **Close without Saving**.

Close the Terminal as before and open a new one. This time, type:
```
sudo update-grub
```
You will be asked for your password at the prompt. Type it, press ENTER and wait for the process to finish. Once the prompt returns to...
```
user-name@computer-name:~$
```
...you should type...
```
sudo shutdown -r now
```
...to restart your computer. You should now be greeted by a new GRUB 2 menu, with your newly added menu entries!

==========================================

P.S. If you do not understand any of the above instructions, I recommend visiting the >>[GRUB 2 Ubuntu Community Help Documentation]("https://help.ubuntu.com/community/Grub2")<< pages.

If you still have no clue what I'm going on about, feel free to reply to this post. I'll be happy to help! If you have other Operating Systems installed, such as Microsft Windows, reply to this post and I'll explain how to do so.

---

### Post by NJPinator on 2011-03-26
It's been a month since a post was made here. Has the problem been solved? If so, be sure to mark this thread as "Solved"!!! This helps others to get advice, and prevents 'spam' from people who think they're helping you, when actually the problem has already been resolved.

---

