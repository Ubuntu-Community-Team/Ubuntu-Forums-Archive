---
title: "Is it possible to run a printing company on Ubuntu?"
date: 2009-11-22
forum: New to Ubuntu
---

### Post by resplence on 2009-11-22
Hello,

I'm not at all experienced with Ubuntu or Linux, but for a variety of reasons I'm thinking of switching the computers in the printing company I just started working for from Windows (3 computers, networked, Vista and XP, used by about 5 people) to Ubuntu. 

The problem is that, in addition to regular office work, we have to do a lot of graphic work, with the Corel and Adobe suite, and I'm not sure if the equivalents in the Linux world are really up to it. 

I mean no disrespect by that, it's just that, for example, Corel and Adobe in theory are supposed to be able to open and edit each other's files as if they were native. In practice, it's a mess, even in Windows. So I have a hard time believing some completely alien software, from another OS, would be able to handle that.

Do you guys have any experience with that? Do you think it's feasible?

Thanks for any input.

---

### Post by yeats on 2009-11-22
Really, I think the only way to find this out is to install Linux (Ubuntu is obviously the preference around here, but there are *many* other options) and try out the Linux "equivalents" to what you're used to using.  I put that in quotation marks because it's important not to expect all Linux/Free/Open Source programs to have all the same features as the proprietary programs you're used to using.  As you say though, if you're already using workarounds with the pricey stuff, it's probably worth it to try out Linux for this. :-)

---

### Post by sandyd on 2009-11-22
> **resplence said:**
> Hello,

I'm not at all experienced with Ubuntu or Linux, but for a variety of reasons I'm thinking of switching the computers in the printing company I just started working for from Windows (3 computers, networked, Vista and XP, used by about 5 people) to Ubuntu. 

The problem is that, in addition to regular office work, we have to do a lot of graphic work, with the Corel and Adobe suite, and I'm not sure if the equivalents in the Linux world are really up to it. 

I mean no disrespect by that, it's just that, for example, Corel and Adobe in theory are supposed to be able to open and edit each other's files as if they were native. In practice, it's a mess, even in Windows. So I have a hard time believing some completely alien software, from another OS, would be able to handle that.

Do you guys have any experience with that? Do you think it's feasible?

Thanks for any input.
it is feasible - depending on what your actually designing.
for a nice long list of graphics applications in Linux see here 
-> [http://linuxappfinder.com/graphics](http://linuxappfinder.com/graphics)

There are also some windows applications that can run in Linux through a program called WINE. 

see [http://appdb.winehq.org/](http://appdb.winehq.org/) for a list of windows applications that work and their rating (garbage, bronze, silver,gold, platinum)

---

### Post by jimmy the saint on 2009-11-22
Personally, I think that attempting to replace a photoshop workplace with an opensource alternative, at the point, will be problematic.  We have the Gimp, which is an outstanding application, but not quite proffesional level yet.  For just about any other workplace environment, I would say go for it, but for intensive graphics work, or similar media production environments, I would say that you are better off with the pro tools.

---

### Post by tgalati4 on 2009-11-22
Take your oldest/crappiest computer--add some RAM and a new hard disk then load Ubuntu Studio.  Play with it for a while and see what works and what's missing then report back.

---

### Post by 3rdalbum on 2009-11-23
I typed up a long message on my mobile phone a couple of hours ago... and lost the connection and therefore the message.

Proprietary software and closed file formats are the order of the day for the printing industry. Too many customers submit their work as Powerpoint or even (don't laugh, it happens) Excel format. The latter is readable, the former is completely useless on Linux unless you're running Powerpoint in Wine.

PDF is completely cross-platform, but you can't trust your customers to make usable PDFs. Many of them have barely grasped e-mail ("Hello, my computer is currently e-mailing you a file, have you started recieving it yet?").

As far as I'm aware, there is no Free Software out there for managing a printing company; no Print Perfect Elite equivilant. And the best free typesetting program for Linux is Scribus, which is a good program but certainly doesn't cut the mustard when you compare it to Indesign.

Adobe has a hundred full-time programmers working on Indesign, and they've been developing it for ten years; unfortunately Scribus can't keep up. I'm not sure of file import capability from Indesign and Quark, but it's probably either not good or not existent.

It would be great if you could give it a little trial run on one computer and see how it goes, and report back; but I really do think it would either be a waste of your company's time, or it would require so much proprietary Linux software that the benefits of switching would be negligable.

Sorry to sound so negative, but this area really is something that hasn't been given a lot of love in Linux and Free Software, probably due to lack of knowledgable people. I mean, you just got a bunch of well-intentioned people replying who think that your business runs entirely on Adobe Photoshop.

If you could learn to code, say in Python, and develop a Print Perfect Elite replacement for Linux, that would be absolutely awesome.

---

### Post by resplence on 2009-11-27
Thanks for all the replies and sorry for the delay. 

I am going to install Ubuntu in my personal laptop and see how far I can get with it. I plan to report back anything eventful.

> PDF is completely cross-platform, but you can't trust your customers to make usable PDFs. Many of them have barely grasped e-mail ("Hello, my computer is currently e-mailing you a file, have you started recieving it yet?").

So true. And I lost count of how many times people asked me if I couldn't just fix the art in the PDF by myself, once I pointed out a problem with how the colors would print or something.

Thanks again.

---

### Post by ukripper on 2009-11-27
Inkscape, GIMP should be able to do most of it.

Also you can see this video which runs corel, photoshop and dreamweaver on ubuntu using wine [http://www.youtube.com/watch?v=8mEo1GXfsTg](http://www.youtube.com/watch?v=8mEo1GXfsTg)

---

### Post by tgalati4 on 2009-11-27
There's more to running a company than just printing.  Customer communication and collaboration are important.

Watch some of the vidoes at 37signals.com.  Such as on this page:
[http://basecamphq.com/?source=37signals+home](http://basecamphq.com/?source=37signals+home)

Although these are closed-source, web-based, software-as-a-service products, there are many equivalents in the open source world.

For instance tracking projects, you can use Tracks, [http://getontracks.org](http://getontracks.org).  I've got the latest Tracks (1.7) running on an old Dapper Drake machine (6.06) using a Bitnami Stack.  You can play with someone else's online server at:

[http://www.gtdify.com/](http://www.gtdify.com/)

For customer relations management (CRM) you can use 37signals.com Highrise product or run your own SugarCRM instance on a local server.  See [http://sugarcrm.com](http://sugarcrm.com)

So, you can run Ubuntu servers and desktops in your business.  It won't cost you much in licensing.  You can purchase support from Ubuntu if you need it, or find a local linux guru.  Do a search for your local linux user group (LUG).

But what tools you ultimately run on those servers and desktops is up to you.  There are both open and proprietary tools to run on Linux to get the job done.  The workflow will be different from your current Windows setup.

Can you grow your printing/design business using exclusively linux-based tools?  That's up to you.  By sharing your experiences, you will both learn and grow.

Don't think of just simple replacements of Windows tools with Linux tools.  Recast how you operate your business and communicate with your customers.  Then you will see the power of gnu/linux, Ubuntu, and open source software in general.

[http://www.gnu.org/philosophy/free-sw.html](http://www.gnu.org/philosophy/free-sw.html)

This describes the 4 software freedoms that most open source projects operate under.  Compare that to the licences of your current software.  

You don't have to be a hostage to someone's software package.

---

### Post by resplence on 2009-11-28
Thanks for that, very eye-opening.

---

### Post by tgalati4 on 2009-11-28
It's much easier to make these changes now when your company is small.  Imagine trying to implement new workflow in a 50-person company.

One major advantage of web-based apps is that your workers can use Mac, Linux, or Windows to collaborate and yet keep their own machines as-is--using the tools that they are familiar with.

You wouldn't pull photoshop from your graphic designers if that is what they have spent years using.  For someone who has learned inkscape/scribus/gimp, giving them photoshop would be just as foreign.

apt-cache search inkscape
apt-cache search scribus
apt-cache search gimp
apt-cache search draw
apt-cache search design
apt-cache search pdf

An interesting inkscape thread:

[http://ubuntuforums.org/showthread.php?t=1311637](http://ubuntuforums.org/showthread.php?t=1311637)

---

