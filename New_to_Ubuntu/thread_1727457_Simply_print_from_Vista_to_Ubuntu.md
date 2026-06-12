---
title: "Simply print from Vista to Ubuntu?"
date: 2011-04-12
forum: New to Ubuntu
---

### Post by 2CV67 on 2011-04-12
I have a Canon printer connected by USB to my dual-boot (Ubuntu/XP) PC, which itself is on a wifi connection.

When I am in XP, visitors with Vista portables can use my printer via a wifi network which was easy to set up Vista/XP.

These days, I am more usually in Ubuntu & the visitors can't print...

I started Googling this topic & got lost in complicated-looking instructions for Samba (which is not yet installed) & clients & servers etc.
In fact, most of the information seems to be for printing from Ubuntu to a printer on a Windows network, rather than the other way round.

What is the simplest, 100% GUI way of printing from a Vista portable to a USB printer on an Ubuntu wifi PC?

Thanks for all suggestions!

---

### Post by pricetech on 2011-04-12
Samba tutorial here:

[http://ubuntuforums.org/showthread.php?t=1644585](http://ubuntuforums.org/showthread.php?t=1644585)

Once installed and running you'll be able to share your printer just like you do in windows

IF

The printer works under Ubuntu.  If not, all the Samba in the world won't help.

---

### Post by walt.smith1960 on 2011-04-12
Can the printer be connected to a network? If so, is it practical for you to run a cable from the router to the printer? Or does the printer support wireless printing?  Canon's Linux support is not as robust as other manufacturers so make sure your printer has Linux support available.  Canon's Asian or European web sites might be better than North American Canon sites. If you can hook the printer to a router, anyone who can connect to your network can print to the printer.  I have no experience with sharing via a USB connection.

---

### Post by crispy_420 on 2011-04-12
First make sure it works in Ubuntu. Once you know it is functional you can let the sharing begin. You mentioned the easy gui way, then install the samba GUI called system-config-samba. That will allow sharing of the printer with a nice and easy GUI.

---

### Post by stmiller on 2011-04-13
Windows (and OS X) can print to cups. No need to mess with samba.

---

### Post by 2CV67 on 2011-04-13
Thanks for the replies so far, which I am still trying to digest.
> **stmiller said:**
> Windows (and OS X) can print to cups. No need to mess with samba.
Can I find any instructions or information on that somewhere?
I did find this:  [https://help.ubuntu.com/community/NetworkPrintingFromWinXP](https://help.ubuntu.com/community/NetworkPrintingFromWinXP)
but it uses Samba & gets messy.

To answer other questions:
1. The Canon iP4300 works OK in Ubuntu (not quite as well as in XP) both using CUPS & using the drivers from Canon Australia.
2. The printer is connected by USB to the main Ubuntu/XP desktop PC.
3. The printer does not have its own wifi capability.
4. The printer is too far from the router for a convenient cable connection.

I don't have any visiting Vista portables here today to test, but if I can prepare, mentally & physically, first...

---

### Post by 2CV67 on 2011-05-11
Well, I spent weeks Googling & reading threads & instructions about Samba.
And got further & further from understanding anything or feeling capable of making it work.

In the end, I decided to just start & in fact it works (too?) easily.

This is my guide to Samba for Dummies.
Please feel free to correct as necessary!

On the Ubuntu machine "DESKTOP":
1. System > Administration > Printing > Printer > Properties > Policies : Check "Enabled & Accepting Jobs & Shared"
2. Synaptic Package Manager : Install "system-config-samba"
3. System > Administration > Samba > Preferences > Samba Users : Select or add one, say "joe" & set password "pw"

On the Windows machine:
4. Navigate to Canon USA & download driver for printer > unzip & put in program files
5. Network > DESKTOP (Ubuntu PC) > Password request > Input "joe" & "pw" ( & check to remember) > shows Printer & Shares OK
6. Control Panel > Devices & Printers > Add a printer > Add a network, wireless or Bluetooth printer > ???
Sorry, I didn't record the next bit in detail, but it just involved selecting the printer & browsing to the driver in Program files.
7. Set new printer as default, if required.

So far, so good.
I can now print anything from the Windows Netbook to the Ubuntu Desktop USB printer.

One surprising thing is that I can also reach DESKTOP & Printer from other Windows users sessions, by entering any old rubbish as username & password...

I really wish there was a Dummy-level Guide to Samba available somewhere, just to cover simple printing & file-sharing.
Nothing I have seen is anywhere near basic enough.

---

