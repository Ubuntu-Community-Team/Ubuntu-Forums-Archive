---
title: "Web developer needs hardware/software support"
date: 2011-02-17
forum: New to Ubuntu
---

### Post by rubhadubh on 2011-02-17
Hi, my win xp pro desktop is nearing retirement and as a full-time web developer this is my main work machine. Despite the windows os, I work in php/mysql and recently changed from iis to apache for my development web server.

I'm wondering if it's a good time to ditch microsoft for the os too. I'm planning to buy a new pc with ubuntu installed and run both for a while, but am a bit clueless as to what spec the new pc should be and what core programs are available. Would a pentium dual core e5500 with 4GB RAM be plenty to run ubuntu for usual developer tools, plus some home recording and typical music/video playback?

The software tools I use most are old versions of dreamweaver and fireworks plus email and multiple browsers. Is there a good php development environment and graphic manipulation software that you would recommend?

I have external hard drives hooked to my win pc for backups and shared network files - would I be able to access these? Read/write?

I can't afford for the move to make too much downtime - am I crazy to consider moving to ubuntu?

Any opinions most welcome! Thanks.

---

### Post by rbishop on 2011-02-17
Ubuntu is a great platform to move to.  One place I would check for the Dreamweaver software would be looking at WINE to make sure that the version you have has been tested/works with WINE.  I used to use MS Frontpage religiously but that fell by the wayside when I started working with Ubuntu,  I actually went to coding by hand, mostly.  There are plenty of programs for Linux that allow you to code in PHP and other languages.  

I made the switch at my house about 2 years ago.  Only time I use Windows is when I am at my job.  I haven't looked back at windows for the house since making the switch.

---

### Post by snowpine on 2011-02-17
Welcome to the forums!

Ubuntu's system requirements [are well-documented]("https://help.ubuntu.com/community/Installation/SystemRequirements"). 

Linux is used on many mission-critical systems where downtime is unacceptable. I think you will be impressed with Linux's stability and efficiency, once you've been through the learning curve and have a system fully customized to your needs.

You might consider a dual-boot with Windows if there are certain Windows tools you need for your work. Or, better yet (this is what I do) run a Windows virtual machine (using VirtualBox or similar) as a "guest" OS inside of Linux.

The possibilities are unlimited, good luck! :)

---

### Post by wormyblackburny on 2011-02-17
Here is what I would do:

Dual boot Ubuntu/Win7 (you may never use 7, but you may as well have it there just in case)

Install Virtualbox in Ubuntu and use it to import your XP machine into a virtual machine. (Why lose everything you already have on the XP box? Virtualbox can take your running machine and make it a virtual machine, then you can tweak your Virtualbox settings and allocate the majority of ram/processor power to the XP image when you are compiling etc... and you get to keep all of the files/programs you already have on the XP box)
[URL="http://www.virtualbox.org/wiki/Migrate_Windows"]
Here is a tutorial on a p2v conversion in virtualbox[/URL]

---

### Post by rubhadubh on 2011-02-17
Thanks folks, the VirtualBox route sounds most popular - what I don't want to happen is that I buy a new pc and then find I don't use it because I can't find apps that allow me to work properly.

I was hoping to switch from my current old software, to something new, but at the moment it's sounding like ubuntu isn't hugely well supported for work apps - is that the case? Recent pcpro test in the uk found that email users coming from outlook couldn't find a decent alternative, for example.

I make my living writing code, so I was hoping for a zipdedo productivity coding platform, but running my clapped out old apps would have to be the way to go?

---

### Post by mcduck on 2011-02-17
> **rubhadubh said:**
> Thanks folks, the VirtualBox route sounds most popular - what I don't want to happen is that I buy a new pc and then find I don't use it because I can't find apps that allow me to work properly.

I was hoping to switch from my current old software, to something new, but at the moment it's sounding like ubuntu isn't hugely well supported for work apps - is that the case? Recent pcpro test in the uk found that email users coming from outlook couldn't find a decent alternative, for example.

I make my living writing code, so I was hoping for a zipdedo productivity coding platform, but running my clapped out old apps would have to be the way to go?

It's pretty much a question of how you want to work, and how attached you are to the Windows apps you have used this far.

If you want WYSIWYG editors like Dreamweavr, you'll probaby have to run Dreamweawer in a virtual machine. if you are like me, and only want a god coding platform for your development, then you'll have no problems doing that with native Linux software, there are plenty of great editors and development tools around.

Same gos with Fireworks and graphics apps, if you want exactly the features and UI you are used to, then you'll have to run the programs you are sued to. On the other hand you can find great programs suitable for professional-level work if you are ready to learn how to use those tools.

(I'm a multimedia/web designer myself, and having learned to do my work with a text editor instead of WYSIWYG tools I had no troubles moving to Linux. And also I've used plenty of different graphics apps on different operating systems over the time so doing the same work with Gimp+Inkscape was no problem either. Most people who have troubles finding suitable tools are the ones who have only ever actually learned how to do their work on one certain program, and who depend on that program instead of having any general skills they could apply with other tools.)

There are plenty of decent e-mail apps available, by the way. Of course if you use Exchange mail instead on normal POP/IMAP account then you might have troubles finding anyhting that works with it as well as Outlook does.

My general advice would be not paying too much attention to what other people say, and instead trying yourself. This of course applies to everyhting I've said as well... :D

If you are ready to learn something new instead of looking for something that would be just like what you've used before, only somehow better, you shouldn't have any troubles doing your work on Linux.

---

### Post by kittkatt on 2011-02-17
Ubuntu can do all the stuff that you specified in your original post with minimal problems, the specs for you new machine are more than enough for the OS system requirements.  

The biggest problem is going to be learning curve and inevitable "Murphy's Law" type stuff that comes up ("what? what do you mean my wifi-card maker didn't release linux drivers?  etc.).

Now normally, it doesn't take too long to get into the swing of how things in Linux works (learning about software repositories, filesystems, permissions etc.), but I'd say if your machine is mission critical, its best to stick with what you know and what is most well supported by the industry.

Assuming you can afford it, I'd say stick with Windows 7, but install Ubuntu alongside as a dual boot, or run Ubuntu as a virtual machine inside Windows 7.  Try and duplicate your setup on Ubuntu during your spare time, once you feel comfortable with how things work, then you will feel a lot more comfortable about switching, in fact you probably will want to switch once you realize the power and increased control you have in Ubuntu.

---

### Post by snowpine on 2011-02-17
Think of Linux as another tool in your toolbox, or another color on your painter's palette. :) If you expect it to be an exact replacement for Windows in every way, you'll be disappointed, but if you think of it as an additional skill you can learn to further your career, you'll be excited! The Internet basically runs on Linux, so I think you'll find it a wonderful platform for coding, email, design, productivity, etc. ;)

---

### Post by rubhadubh on 2011-02-17
I reckon my plan to keep my existing winxp box running and buy a new ubuntu box, running both with a kvm switch is going to be the way to go. I don't really want to clog up a new pc with all my legacy crap, but neither can I afford to be without it.

If the ubuntu install doesn't work out, I can always install win7 instead.

I only use dreamweaver in code view, building all my sites by hand - I don't use a fraction of the facilities, but I do like the code colouring, and 'predictive' text. Can you suggest some alternatives for that?

In Outlook 2003 I have multiple inboxes and rules that filter incoming mail. I do use the calendar, but not much else. Can Thunderbird or Evolution handle that much?

I have GIMP installed on my current pc, but prefer fireworks so far - maybe I just have to get used to it!

---

### Post by mcduck on 2011-02-17
> **rubhadubh said:**
> I reckon my plan to keep my existing winxp box running and buy a new ubuntu box, running both with a kvm switch is going to be the way to go. I don't really want to clog up a new pc with all my legacy crap, but neither can I afford to be without it.

If the ubuntu install doesn't work out, I can always install win7 instead.

I only use dreamweaver in code view, building all my sites by hand - I don't use a fraction of the facilities, but I do like the code colouring, and 'predictive' text. Can you suggest some alternatives for that?

In Outlook 2003 I have multiple inboxes and rules that filter incoming mail. I do use the calendar, but not much else. Can Thunderbird or Evolution handle that much?

I have GIMP installed on my current pc, but prefer fireworks so far - maybe I just have to get used to it!
Even the default text editor in Ubuntu (Gedit) handles syntax highlighting, and also supports plugins (so you can use code snippets, or [zencode]("http://code.google.com/p/zen-coding/"), if you just enable/install a plugin you like.)

Of course there are more advanced editors with more project management features available if that's what you want. :)

Evolution handles multiple inboxes and mail filtering, plus has a calendar & tasklist which both integrate pretty well with the rest of the desktop. If you find that you don't like Evolution , then Thunderbird + Lightning is also a popular choice.

I don't think there's any combined bitmap/vector app quite like Fireworks, but Gimp does bitmap graphics very well, and I use Inkscape for vector graphics (I actually prefer it over Illustrator these days, and use it on OSX as well as long as the work I'm doing at the moment doesn't require me to share source files with Illustrator users). And since you do coding, you might also enjoy Imagemagick, although being a command-line image editor it definitely has a bit of a learning curve (on the other hand being able to script graphics processing opens a whole new world of options... ;))

---

