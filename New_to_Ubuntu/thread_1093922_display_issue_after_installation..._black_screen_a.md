---
title: "display issue after installation... black screen and nowhere to go!"
date: 2009-03-12
forum: New to Ubuntu
---

### Post by razorw_k9 on 2009-03-12
after completing the xubuntu installation (with life cd on text mode), the system asked me to restart the computer... things were going well up to that point!

when i clicked the message to "ok" the restart of the computer, my screen went black and gave a message saying: "cannot display this video mode, change computer display input to 1280x1024 @ 60hz."  since i have been dealing with this issue even before completing the instal, i knew that i could just hit "esc" then take out the cd and hit any key and the system would restart (i could not see those messages 'cuz of the black screen but i remember them from a previous try).

i restarted the computer with and without the live cd to see if i could get to a text prompt but that did not work.  with the live cd i get back to the instal menu.

is there any way to get a prompt where i can type a "sudo" command to set up the display?  i have seen some thread messages talking about opening a "terminal window" to run the following:

---------from [http://ubuntuforums.org/archive/index.php/t-166.html--------](http://ubuntuforums.org/archive/index.php/t-166.html--------)

sudo nano /etc/X11/XF86Config-4
Look for this line: XX will be 16, 24, 32 etc..
DefaultDepth XX
Then look for the section to match it: Mine is set to DefaultDepth 24 so mine looks like:
SubSection "Display"
Depth 24
Modes "1280x1024" "1024x768" "800x600" "640x480"
EndSubSection
This makes 1280x1024 the primary resolution. You can adjust that line accordingly to suit your needs. :)

--------end of quoted post

another post talked about using the "sudo dpkg-reconfigure xserver-xfree86" line to get to configure the resolution but i cannot get to a prompt where to try either one of the suggestions.

any ideas/suggestions?  -thanks

---

### Post by bailbath on 2009-03-12
You can use the rescue mode in grub to get to a menu that includes Xfix to get a working X or you can drop to a root terminal to follow a tutorial to fix it yourself.
To fix it yourself you need to know the problem to find the problem we need to know your hardware including what monitor.
To get to grub menu you need to hit a button as your pc boots just after the bios screen. Then highlight the rescue mode and hit enter.
Ian

---

### Post by razorw_k9 on 2009-03-13
thanks for your reply!

i tried restarting the computer one more time with the life cd and i was able to go into the "try xubuntu without changing anything" option.  mind you that prior to that, several tries ago, i was able to install xubuntu with the text mode menu (see initial post).  while in the "try xubuntu without changing anything" i went through the "install" once again by double clicking in the icon on the desktop.  the process started, i got the message that xubuntu was now installed and i had to restart the computer.  i restarted it without the life cd in and NOPE!  xubuntu would not boot.

i tried changing the boot order in the bios... (e.g.  c,a,cdrom... scsi,a,cdrom...) and nothing!  the message says that i cannot boot.

i can see the drive when i go in xubuntu with the life cd and it does look like the os IS installed in the harddrive but i cannot find the harddrive.  does the installation assign "c" as the letter for the drive automatically?  i tried booting with a 6.22 boot disk and it looks like s: and r: are assigned to "something" but i cannot access any directories using dos.

any suggestions?

---

