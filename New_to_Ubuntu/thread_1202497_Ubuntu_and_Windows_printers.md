---
title: "Ubuntu and Windows printers"
date: 2009-07-02
forum: New to Ubuntu
---

### Post by swappa on 2009-07-02
**Hello there**
I have been using Ubuntu for a few years at home without any issues.
I recently kicked out Vista on my work laptop (running it as a virtual machine) and decided to go for a x64 bit version of ubuntu jaunty. For the most part, it works well. Really well. Even my dual screen setup worked (nearly) out of the box. Well done. 

Most of my work is done through my Vista virtual server though, but I find myself doing more and more from Ubuntu.

Here is the issue; printing on a Windows network. Don't even get me started on this one. Granted, I am not the most Linux savvy person out there and, there are probably thousands of hacks available, but WHY cant I even browse the windows printers on our win2003 file server? I can from my MAC and from my Vista computer. I am on the domain, I can access the shares, but where are the printers? Why does my Ubuntu printing application by default start scanning the network and eventually die? It just says "searching for printers" and then after 10 minutes rolls over and die... Why cant I choose which IP/server name/printer name I would like to add directly? This is not a driver issue since I haven't even gotten to the actual printers yet (yes, looking forward to that too...) so what could be causing this? 

I can add a local printer without any problems.

Sorry for the rant. Big fan of Ubuntu. Just frustrated about this printing stuff...

Thanks..

;)

---

### Post by austinpsycho on 2009-07-02
it dies out?  that sounds like a problem with cups; not with linux design...
did you try updating cups?

---

### Post by Jerry N on 2009-07-02
Ubuntu (and LinuxMint) seems to be real stupid when it comes to finding printers on a Windows server.  I find that I have to go through the "Add Printer" routine to the "Windows Printer VIA SAMBA" section and enter the server and share name manually.  Then I have to tell it what kind of printer it is so it can load the driver.  My experimental Win 7 RC installation found all three Windows printers automatically.

Jerry

---

### Post by Mark Phelps on 2009-07-02
> **Jerry N said:**
> Ubuntu (and LinuxMint) seems to be real stupid when it comes to finding printers on a Windows server.  ...  My experimental Win 7 RC installation found all three Windows printers automatically. Jerry

That's because ... wait for it ... Win 7 is "MS Windows"!!!

Personally, I think we should give the Samba folks credit for even figuring out a way to network Linux machines with MS Windows machines.  The fact that it takes a few entries and mouseclicks to make it work is trivial.

---

### Post by DownTown22 on 2009-07-02
> **Mark Phelps said:**
> That's because ... wait for it ... Win 7 is "MS Windows"!!!

Personally, I think we should give the Samba folks credit for even figuring out a way to network Linux machines with MS Windows machines.  The fact that it takes a few entries and mouseclicks to make it work is trivial.

Trivial? No...no it isn't.
This all goes back to making Ubuntu more user-friendly.  If you really want to convert the masses, it's little things like this that need to be fixed.  The amount of little things that are annoying with Ubuntu is rediculous (and no, I'm not the only one who finds little things annoying).

It's obvious that pretty much all the bigger things in Ubuntu have been ironed out and it's rock solid!  It's all these little things, that once fixed, will make Ubuntu even better.

And I don't need a response to this saying how Windows/OSX/Linux are different and you have can't expect things to be the same, and so on and so forth.

---

### Post by caravel on 2009-07-02
You have to face facts:  Windows interoperability is not that important to most UNIX/Linux users and it's certainly not important to MS themselves.

---

### Post by DownTown22 on 2009-07-02
> **caravel said:**
> You have to face facts:  Windows interoperability is not that important to most UNIX/Linux users and it's certainly not important to MS themselves.

I find that hard to believe....

I think I'd need a little more evidence that one statement.
Might have to poll this one.

[http://ubuntuforums.org/showthread.php?t=1202605]("http://ubuntuforums.org/showthread.php?t=1202605")

---

### Post by Jerry N on 2009-07-02
"*You have to face facts: Windows interoperability is not that important to most UNIX/Linux users and it's certainly not important to MS themselves.*"

I must respectfully disagree.  Interoperability can be _very_ important to serious computer users looking at the potential of Linux as an alternative.  The fact is, many Linux users and experimenters are pragmatists, not fanatics. 

Jerry

---

### Post by superprash2003 on 2009-07-02
you do get an option to manually insert the ip address of the machine with the printer and specify it using its ip.. check out the screenshots here [http://www.prash-babu.com/2008/07/how-to-connect-to-network-printer-in.html](http://www.prash-babu.com/2008/07/how-to-connect-to-network-printer-in.html)

---

### Post by swappa on 2009-07-02
> **superprash2003 said:**
> you do get an option to manually insert the ip address of the machine with the printer and specify it using its ip.. check out the screenshots here [http://www.prash-babu.com/2008/07/how-to-connect-to-network-printer-in.html](http://www.prash-babu.com/2008/07/how-to-connect-to-network-printer-in.html)

Thanks. Will try that tomorrow at work. Samba seems to be the way to go.
For sake of usability; Yes- these things gotta work straight out of the box. I can take a driver issue, no problem, I have that on Windows as well, but when Ubuntu fails to locate any printers at all (we have 30 of them on our network) it is, sadly, a failure. More importantly, it will scare away any potential Ubuntu/Linux user out there. I have a few of them around me at work and they weren't impressed when Ubuntu couldn't locate the printers. Cover the basics first....make sure they work. 

Thanks for your input people. Really appreciated. 

:-)

---

### Post by swappa on 2009-07-03
Wanted to provide an update;

Going with Samba took care of business.
I can now print, even with color, which I cant from my Vista x64 bit workstation. I downloaded a custom PPD from [www.linuxprinting.org](www.linuxprinting.org) since the automatic download and install driver function didn't work. So problem solved, but I find there is room for improvement with regards to the printing features. 

Thanks for your input.

):P

---

