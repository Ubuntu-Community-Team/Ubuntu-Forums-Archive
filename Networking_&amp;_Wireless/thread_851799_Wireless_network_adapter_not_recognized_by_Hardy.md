---
title: "Wireless network adapter not recognized by Hardy"
date: 2008-07-07
forum: Networking &amp; Wireless
---

### Post by bravo331 on 2008-07-07
Hello all,
I have been scouring this archive thread all weekend [http://ubuntuforums.org/showthread.php?t=571046](http://ubuntuforums.org/showthread.php?t=571046) trying to solve the exact problem the archive thread describes. I am having the same problem as the person who did post #65. I have downloaded the modified driver; what now? I am pasting the commands from these directions in terminal:

How do I compile the driver?
Unpack the driver:
  tar xvfz rtl8187b-modified-dist.tar.gz
Change into the driver source directory:
  cd rtl8187b-modified
Compile the driver (note, there are a hell of a lot of warnings):
  ./makedrv
To load the driver:
  ./wlan0up

  I am getting the same errors as shown in post #65 of the thread I mentioned. I don't know what any of this stuff like"root" or "compile the driver" or "change into the driver source directory" means. Could someone please direct me to a place where I can learn about all this stuff?  Any help would be greatly appreciated. My laptop has the realtek rtl8187b wireless 802.11g 54mbps usb 2.0 network adapter. Ubuntu doesnt even recognize it. I can connect to the internet wired no problem. As i said my problem is the exact prob that the archive thread refers to..

---

### Post by AndyCee on 2008-07-07
While I don't have answers, I can simplify your problems.

To "be root" is to be the administrator - all powerful with all access to everything on the computer. This is locked down a bit, so that you can't easily bugger up system settings.

To "become root" (or the Ubuntu "superuser") prefix any command with "sudo".
eg: $ sudo ./makedrv

As drivers for most hardware are designed to work in windows, many don't work natively in Ubuntu. "ndiswrapper" is an application which makes the driver run, thinking it's running in windows.

The errors post #65 was getting are due to typos. Use the tab key for autocompletion of long filenames.

---

### Post by bravo331 on 2008-07-08
Thanks for responding!

See thats what I don't understand. How do I use the tab key for auto completion? When do I hit the tab key? Do I type a little of the filename then hit tab? I copied and pasted the comand exactly how it was written in the instruction set for the driver; is the instruction wrong? How does ndiswrapper work? I believe the driver in question is actually a modified linux driver but I want to learn about ndiswrappeer anyway. Ndiswrapper is  an application so I can find it in add-remove or synaptec? I will google it and try to find out about it I guess. Anyway where can I go to learn about all this? The forums are great to search on specific issues but is there a site or something that will help me learn stuff beyond the basics?

---

### Post by AndyCee on 2008-07-22
Sorry for the late reply:

Tab autocompletes like this:

```
$ evolu
```

Press tab

```
$ evolution
```

or

```
ls /boot/grub/men
```

press tab

```
ls /boot/grub/menu.lst
```

So when you have a long, complicated filename/command such as "tar xvfz rtl8187b-modified-dist.tar.gz"

you're better off doing:

```
$ tar xvfz rt1
```

then press tab. The reason for this is that in the situation given, the name of the file shown to you may be slightly different to yours (ie. the 'b' may have been updated to a 'c' or something).

You most certainly can learn beyond the basics. I don't remember how I learnt things like autocomplete with tab, but there are a few ways to learn more and the obvious are often the best. As Ubuntu, and linux in general, has so many varied features, it's hard to find or make useful consolidated information about 'linux'. Anyone feel free to correct me. I've usually had to look for info, and I've learnt many things about linux when looking for a specific piece of info.

For example, when troubleshooting a printer, I learnt about port configurations, lshw, lsmod, print drivers in linux and CUPS, and samba.

My greatest sources of information, in no particular order, are:

[LIST]
[*]Ubuntuforums.org
[*]google.com
[*]man pages for a given command, [eg. tar] type "man tar" in terminal. Unfortunately these pages are often hard to read.
[/LIST]

This thread also contains some links to useful "learning linux" sites:
[http://ubuntuforums.org/showthread.php?p=5334642](http://ubuntuforums.org/showthread.php?p=5334642)

I'm not personally familliar with ndiswrapper, but it is available in the Ubuntu repositories (get it from synaptic).

Hope this helps,
-AndyCee

---

