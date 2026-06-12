---
title: "Antivir help"
date: 2009-09-02
forum: New to Ubuntu
---

### Post by scared0o0rabbit on 2009-09-02
So I've decided I should install an antivirus solution because I do have a drive on the computer that is accessible by both my ubuntu install and my windows install.  I went with antivir, downloaded the tar, extracted it, and ran the install script.   During the process it asked if I wanted to install dazukoFS and all that as well, which is something I've read I would need for antivirus software to work.  I was able to update antivir as well.  However I can't for the life of me figure out how to get the gui open.  The one place I've seen with instructions on how to do it just says to sudo antivir -gui but when I try and do that it just says command not found.  I'm guessing that's the correct command, but I don't know where it's located to actually try it.  Does antivir get 'installed' in the same directory I extracted the tar to, or does it install to some other location by default?

---

### Post by NoaHall on 2009-09-02
Open the terminal, and type "antivir" and then use tab to see any options.

---

### Post by running_rabbit07 on 2009-09-02
See the Ubuntu Security link in my signature and find out everything you could possibly want to know about anti-virus and other security solutions for Ubuntu.

---

### Post by scared0o0rabbit on 2009-09-02
Okay, so reading through that, I've decided I don't need antivir on my ubuntu install, the install on my windows partition is enough.

I've heard some back and forth on the use of a hosts file in linux.  I personally use one in windows, and there's a trick to deal with the issue of it taking a long time to look up DNS info.  Is there something like that I can do in ubuntu?  Also there's a link to a script that appears to update your hosts file for you, is the server that it gets it's information from updated ever do you know?  I'm just curious if this will result in me having a big hosts file that blocks a bunch of now defunct stuff heh.

---

### Post by scared0o0rabbit on 2009-09-02
So I ran the uninstall script that was unpacked in the tar also when I went to install antivir.  It said I had 2 products installed: Guard and Scanner.  I specified Guard for the script since I had to pick one or the other, and after asking me if I wanted to back up a bunch of stuff like my configs for it and my logs, it appears to have uninstalled.  When I try and run uninstall again to uninstall the scanner this time, it appears to have been removed as well when I removed guard.  Is that all I needed to do to remove it?  I don't see anything that appears to be related to antivir in my system monitor as far as running processes.

---

### Post by lisati on 2009-09-02
> **scared0o0rabbit said:**
> So I've decided I should install an antivirus solution because I do have a drive on the computer that is accessible by both my ubuntu install and my windows install.  I went with antivir, downloaded the tar, extracted it, and ran the install script.   **During the process it asked if I wanted to install dazukoFS and all that as well, which is something I've read I would need for antivirus software to work.**  I was able to update antivir as well.  However I can't for the life of me figure out how to get the gui open.  The one place I've seen with instructions on how to do it just says to sudo antivir -gui but when I try and do that it just says command not found.  I'm guessing that's the correct command, but I don't know where it's located to actually try it.  Does antivir get 'installed' in the same directory I extracted the tar to, or does it install to some other location by default?

I'm getting immediate alarm bells here: a simple AV scanner should not need you to install all sorts of other stuff, particularly if it "messes" with your computer's file system. **None of the AV products I've used have needed to change or enhance the file system of my machines.**

---

### Post by scared0o0rabbit on 2009-09-02
The tar I downloaded was from a source I would believe is good.  I got there from a link to avira antivir found on ubuntu.com and it matched up with the URL I'm familiar with from windows.  I would assume that dazukoFS is still present on the system, which is really the only other thing that I think it installed.  Will it harm anything leaving it there, or is there a way to remove that as well?

---

### Post by NoaHall on 2009-09-02
I shouldn't worry about it - it sounds like it DID need it, to access the servers/files on the servers (antivirus app's servers, that is.)
If you want, you can try "sudo apt-get remove --purge dazukoFS"

---

### Post by FreewheelinFrank on 2009-09-02
dazukoFS is for on-access file scanning- Antivir will scan every file that's opened- not really needed unless you're running a server and need to scan files passing through.

Antivir on-demand is all you need really.

You can create a menu launcher for the program in System>Preference>Main Menu using 'New Item'.

The problem with Antivir free is it doesn't allow you to select what to scan- it'll scan *everything*, starting with the Windows partition if there is one.

avast! free doesn't have that restriction- it also has a script to add a menu launcher, and good detection. Unfortunately, it doesn't have incremental updates, so the update process can take a while- bit of a pain if you just want to check your USB after inserting it in an orifice on a Windows machine in an act of unprotected sex- but Antivir doesn't even give you the option of scanning just the USB drive.

---

### Post by scared0o0rabbit on 2009-09-02
> **FreewheelinFrank said:**
> dazukoFS is for on-access file scanning- Antivir will scan every file that's opened- not really needed unless you're running a server and need to scan files passing through.

Antivir on-demand is all you need really.

You can create a menu launcher for the program in System>Preference>Main Menu using 'New Item'.

The problem with Antivir free is it doesn't allow you to select what to scan- it'll scan *everything*, starting with the Windows partition if there is one.

avast! free doesn't have that restriction- it also has a script to add a menu launcher, and good detection. Unfortunately, it doesn't have incremental updates, so the update process can take a while- bit of a pain if you just want to check your USB after inserting it in an orifice on a Windows machine in an act of unprotected sex- but Antivir doesn't even give you the option of scanning just the USB drive.


So... was what I did above adequate to disable and remove antivir?

---

### Post by FreewheelinFrank on 2009-09-03
Follow this guide.

[http://forum.avira.com/wbb/index.php?page=Thread&threadID=29312](http://forum.avira.com/wbb/index.php?page=Thread&threadID=29312)

---

