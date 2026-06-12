---
title: "How to open .vsd file in Ubuntu 8.04"
date: 2009-06-01
forum: New to Ubuntu
---

### Post by atish.sihi on 2009-06-01
Kindly let me know how to open Microsoft Visio (.vsd) file in Ubuntu 8.04.
 Regards,
atish Sihi

---

### Post by steeleyuk on 2009-06-01
I don't think there's any perfect solution. [Though this might help]("https://answers.launchpad.net/ubuntu/+question/18901"), it looks like it might be some work.

---

### Post by jou770d on 2009-06-01
Weird enough, yesterday, I've been searching for a way to do that myself (except that I'm running 9.04).
Anyway, I didn't find a way to do that directly. Only workaround that I found was this:
- Convert the .vsd file to .vdx using [this site]("http://www.conceptdraw.com/en/visio/"). It took them a good 15 hours to actually send me the converted file, I'm not sure if that's normal or if there was any kind of issues this time. I asked the people I'm working with to use vdx files directly to save me the hassle and I'm going to install Visio on a VM in case they forget to do that.

- Now you can open that file using [Dia]("http://live.gnome.org/Dia/"). It's available in Jaunty's repos, not sure about Hardy's but if it's not you can download it from the link.

I hope this helps.


(By the way, I did look into SK1 (linked in previous post) yesterday but couldn't get it to open .vsd files).

---

### Post by Mark Phelps on 2009-06-01
> **atish.sihi said:**
> Kindly let me know how to open Microsoft Visio (.vsd) file in Ubuntu 8.04.
 Regards,
atish Sihi

Ordinarily, you could install Wine and use it to install Visio and use that to open the file, but the only versions of Visio listed in the CodeWeavers application compatibility database are old versions (2003 and prior) and they have low ratings (silver and bronze).

So, it looks like your best option would be to do the file conversion previously mentioned.

---

### Post by Mornedhel on 2009-06-01
> **Mark Phelps said:**
> So, it looks like your best option would be to do the file conversion previously mentioned.

I concur.

While at school I have had to work with several I-only-use-Office-07 students. They wouldn't even save to .doc format, they insisted on .docx, which was a nightmare for me since OpenOffice.org was at the time far from being able to render them properly. Obviously, they also used Visio for everything.

I tried coaxing them into converting to plain-XML Visio (the aforementioned vdx). I tried running Visio (why no, a legit copy, my school had an MSDNAA program) through Wine. In the end what worked best was a Visio install in a fresh Windows XP running within a Virtualbox virtual machine.

---

### Post by jou770d on 2009-06-01
> **Mornedhel said:**
> I concur.

While at school I have had to work with several I-only-use-Office-07 students. They wouldn't even save to .doc format, they insisted on .docx, which was a nightmare for me since OpenOffice.org was at the time far from being able to render them properly. Obviously, they also used Visio for everything.

I tried coaxing them into converting to plain-XML Visio (the aforementioned vdx). I tried running Visio (why no, a legit copy, my school had an MSDNAA program) through Wine. In the end what worked best was a Visio install in a fresh Windows XP running within a Virtualbox virtual machine.

That works as well. But, personally, I prefer to keep my contact with windows as minimal as possible when I have the choice. But I see why you would prefer the VM in your case since your "team" aren't planning on being helpful. 

Plus, it seems that the long delay in the online conversion method wasn't the normal delay. I just tried converting another file right now and it only took about 5 minutes (might have something to do with the fact that I tried sending the file as an email attachment to them instead of using the site upload as I did the last time).

---

### Post by jabbar on 2009-07-07
FYI - there is a visio converter that converts *.vsd files to *.vdx. It appears in ubuntu 9.04. 

It's called "vsdump" - search for it in synaptics.

---

### Post by yinas on 2010-03-25
vsdump found in synaptics, installed
now what?
vsdump --help will only give me "--help" as OPTION
but no hint on usage, and doesnt seem to be as easy as
vsdump MyVisio.vsd NewVisio.vdx

anyone succeeded so far?

---

### Post by jou770d on 2010-04-02
> **yinas said:**
> vsdump found in synaptics, installed
now what?
vsdump --help will only give me "--help" as OPTION
but no hint on usage, and doesnt seem to be as easy as
vsdump MyVisio.vsd NewVisio.vdx

anyone succeeded so far?

Check the manual page:
```
man vsdump
```

Seems like the right way to do it is:
```
vsdump dump [filename]
```
And the correct (although unorthodox) way to get help is actually:
```
vsdump help
```

However, I don't seem to have any Visio files around right now, so I couldn't try it out for myself.

If someone gives it a shot, please do post back here.

---

### Post by spegru on 2010-05-28
Hi I just tried his with a visio file I'd like to open.
Seems to work when you enter command: vsdump dump <filename>
Creates a nice big folder full of ole files.
Problem now is i don't know what to open the files with!
I presume it's xml - but what graphics program understands that?

---

### Post by spegru on 2010-08-02
I found a round about way to sort this.
I found this website [www.freepdfconvert.com](www.freepdfconvert.com)
It converts almost any file into a pdf, including Visio.

It worked very well on the drawing I tried, and of course you can extract parts of the pdf, such as images or text from pdf docs, using many linux based pdf viewers (although I notice that the default evince doesn't seem to do images so try acrobat or xpdf for that)
Since they collect your email address during the conversion, presumably this could result in some kind of spam or other sales related emails heading your way aftewards, but not so far, in my case anyway.

---

### Post by |Eric| on 2010-11-15
seams its not compatible with the visio file i have

---

### Post by ajarmoniuk on 2011-03-15
Use Visio Viewer with Wine:

[http://www.microsoft.com/downloads/en/details.aspx?FamilyID=f9ed50b0-c7df-4fb8-89f8-db2932e624f7&displaylang=en](http://www.microsoft.com/downloads/en/details.aspx?FamilyID=f9ed50b0-c7df-4fb8-89f8-db2932e624f7&displaylang=en)

---

### Post by spegru on 2012-02-16
The really great news is that the very latest LibreOffice 3.5 can now open vsd Visio files. Only tried it once so far but it worked perfectly!
An from there you can save into ODG (yeah vsd would have been nice perhaps) or into PDF

Great stuff

---

### Post by jelevin on 2012-03-20
The new LibreOffice worked perfectly for me also.  Ubuntu 11.10

---

