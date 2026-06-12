---
title: "IE Required How To?"
date: 2011-01-18
forum: New to Ubuntu
---

### Post by ibrrfarr on 2011-01-18
I've read through just about all the IE threads and cannot find anything spot-on, so I am going to give a detailed background.

I use my Ubuntu platform to run all my business.  I am in home inspections for real estate companies, financial institutions and the US Government.

My issue is this:  for HUD database access, US financial database access (B of A, Regions, etc.) and for *some* real estate firms (local ones accessing national databases) Internet Explorer is the **ONLY** web browser that works.

By this I mean that I can access the sites through Firefox (which is what I normally use).  I can log in and bring up the first screen.  When I attempt to upload photos, enter data or really *anything*, none of the features which allow me to 'pull' the material from my computer into their server(s) are displayed.  Regardless of what is and is not being reported, the above sites *I *access are *dependent *upon IE 7.

This is the meta text from one site with the company's name redacted:[INDENT]<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.0 Transitional//EN" > 
<HTML> 
    <HEAD>
        <title>**REDACTED** - Vendor Management</title> 
        <meta content="Microsoft Visual Studio .NET 7.1" name="GENERATOR"> 
        <meta content="C#" name="CODE_LANGUAGE"> 
        <meta content="JavaScript" name="vs_defaultClientScript"> 
        <meta content="http://schemas.microsoft.com/intellisense/ie5" name="vs_targetSchema"> 
        <LINK href="Main.css" type="text/css" rel="stylesheet"> 
        <script type="text/javascript"> 
            if(top!=self) 
                top.location.href=self.location.href 
        </script>

[/INDENT]This is the other site:
 [INDENT]<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd"> 
[/INDENT][INDENT] <html xmlns="http://www.w3.org/1999/xhtml"> 
<head><link href="StyleSheet.css" rel="stylesheet" type="text/css" /><title> 
    Field Vendor Login 
</title> 
<script type="text/javascript"> 
function DoNothing()

[/INDENT]I added this as I thought maybe a programmer might be able to understand something from the code.

Anyway, where I am at is that the WineHQ emulator doesn't help nor does the script add on for Firefox.

I am hopeful that someone might have some insight here as there is a TREMENDOUS interest in Ubuntu with my fellow contractors; however, we are currently having to do some work with Ubuntu and then come home and use another computer to simply upload our data.

Thanx for taking a look!

---

### Post by bro on 2011-01-18
Some sites might use code that only works with ie. Fortunately less every day, but on some old intranets you might be stuck. There is not much you can about it except complain with the owners of the site and/or use ie. 

To use ie in ubuntu you could try this: [http://www.tatanka.com.br/ies4linux/page/Main_Page](http://www.tatanka.com.br/ies4linux/page/Main_Page) it'll probably work, but it is intended more to test websites, not for real safe browsing. Another route we be to virtualize windows and use when you really need it.

---

### Post by bro on 2011-01-18
Some sites might use code that only works with ie. Fortunately less every day, but on some old intranets you might be stuck. There is not much you can about it except complain with the owners of the site and/or use ie. 

To use ie in ubuntu you could try this: [http://www.tatanka.com.br/ies4linux/page/Main_Page](http://www.tatanka.com.br/ies4linux/page/Main_Page) it'll probably work, but it is intended more to test websites, not for real safe browsing. Another route we be to virtualize windows and use when you really need it.

---

### Post by Frogs Hair on 2011-01-18
Give this add-on a try , I know it works for some users . After installing right click the Firefox panel and select customize and drag the menu applet from the panel. [https://addons.mozilla.org/en-US/firefox/addon/user-agent-switcher/developers](https://addons.mozilla.org/en-US/firefox/addon/user-agent-switcher/developers)

---

### Post by HereInOz on 2011-01-18
Another option is to purchase a copy of Crossover Linux from Codeweavers.

[http://www.codeweavers.com/](http://www.codeweavers.com/)

This will allow you to run IE and a host of other Windows software on a Linux machine, without having to go to a virtual machine scenario.

Crossover doesn't work all that well with MS Access, but it is fine for all the rest of the Office offerings, and IE.

Costs a few dollars, but it may be worth it for you.

Cheers,

Alan.

---

### Post by ibrrfarr on 2011-01-18
Thank you all for replying!  I will check all options out and report back accordingly.  I am not opposed to the CrossOver, even though it costs.  My reasoning is that even though open source is predominately free it still takes infrastructure investment, so to speak.  Being that I am capitalizing on the technology, the price is well worth the investment should it work.

---

### Post by JKyleOKC on 2011-01-18
Still another solution, that might be viable for your needs, would be to install VirtualBox from the repositories on your Ubuntu machine. This is a program that lets you create "virtual machines" that act just like real machines, only they are a bit slower since every individual operation has to be translated from the VM over to the actual host machine to be executed. With modern hardware (1 GB or more of RAM and dual-core or better processor) the slowdown is almost unnoticeable, though, in my experience with it.

The VM will have its own virtual drive(s) which are actually individual files on the host machine, and have no other connection with your actual drives. You specify the drive's size when creating the VM, and initially it's totally blank so of course the VM cannot do anything but complain that it has no operating system.

At that point, you install an actual copy of the Windows version you prefer; XP Pro works nicely, as does Windows 2000 Pro. Once that is done, you can launch the VM and have it running as "just another program" on the Ubuntu box, and can transfer files between Ubuntu and Windows by using vbox's "shared folders" feature.

I'm using this approach in my data recovery business; almost all of my customers use Windows and Windows-only programs. I have five VMs on this machine, one for each specialized need. All five are in "saved" state (like hibernation) most of the time but I launch one when needed, use it, then put it back to sleep. It's definitely worth looking into and the "virtualization" forum here offers lots of help getting started...

---

