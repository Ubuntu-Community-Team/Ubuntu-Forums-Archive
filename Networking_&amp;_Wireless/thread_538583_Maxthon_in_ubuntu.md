---
title: "Maxthon in ubuntu?"
date: 2007-08-30
forum: Networking &amp; Wireless
---

### Post by yehudaco on 2007-08-30
can i use maxthon 2.0 on ubuntu fiesty - replace the firefox with maxthon...
can i? can i?

---

### Post by init1 on 2007-08-30
> **yehudaco said:**
> can i use maxthon 2.0 on ubuntu fiesty - replace the firefox with maxthon...
can i? can i?
It's possible. I was able to install it, but not to run it. I'll try again.

---

### Post by yehudaco on 2007-08-30
i'd love to hear about your experience with it..!!

---

### Post by sawjew on 2007-08-30
I doubt you will get Maxthon to work on any Linux system as it is only a different interface on Internet Explorer so it will not work unless you have IE installed first.  You may be able to get IE working on Wine or Crossover and then install Maxthon but it would not be recommended as you will have all the security breaches of IE without any of the Windows Update patches or antivirus/firewall to protect your system.


Fortunately if anything did get through it would only affect wine not your base linux system.  

You would be better off using one of the native browsers like firefox, epiphany, konqueror, opera or one of the many others available for linux.

---

### Post by init1 on 2007-08-30
No, I can't run it in wine.

---

### Post by yehudaco on 2007-08-30
so be it....allthough it a shame... it is an excellent browser...

---

### Post by callan79 on 2007-08-30
> **yehudaco said:**
> can i use maxthon 2.0 on ubuntu fiesty - replace the firefox with maxthon... can i? can i?

Hi There,

I've been using Ubuntu for almost 18 months now, and I have not looked back, it's awesome. But before I discovered Ubuntu, I was using Windows XP and I thought Maxthon was the best thing in the world, and it took some patience to get used to Firefox.

I did some messing around, and worked out that in Firefox you should install these addons (plugins) :

  -  download statusbar
  -  tax mix plus (lets you customise your tab behaviour, just like you can in maxthon)
  -  fireform (lets you save your name and address for online forms)

Once I got those plugins going and configured to my liking, it still took me perhaps 2-3 weeks to be happy with Firefox, and now I hate Maxthon / IE with a passion!

Also remember there are tons of other browsers out there (Konqueror, Swiftfox, Opera ...) but I've never had a need to look at them, as Firefox now does all the things that I loved about Maxthon. Oh by the way in Tab Mix Plus, enable the session manager :)

And, another success story - my partner used Avant Browser, basically the same as Maxthon. I installed Ubuntu for her, FORCED her to use it, and after 2 weeks of complaining, she's now realised that it's actually quite good!

Cheers
Callan

---

### Post by por100pre1 on 2007-08-30
> **yehudaco said:**
> so be it....allthough it a shame... it is an excellent browser...

Maybe it's time to move on, have you tried Opera?

---

### Post by Culprit on 2007-08-31
I have Maxthon 2 installed, but it did no work.
When I try to run under wine using ies4linux installation I become message "This program could not be run under Win95 and Win3.x". Maxthon 2 is using MFC42u.DLL which is unicode library. ies4linux is designed for ANSI.

When I install under wine, where I copy all files from IE, than I run Maxthon 2, but I become Maxthon Error message, which not allow to continue.

---

### Post by tomviolin on 2007-09-02
I need to use IE to access one or two sites that don't work under Linux Firefox.  Rather than always having to launch VMware, I am using Crossover to run IE.  I was able to then install Maxthon "classic version" [Maxthon 2 was a complete no-go] and it works well, except that the display of the tabs is a little off, and any skin looks and operates terribly.  Switch to "no skin" and you should be set.

As I said, I only use IE/Maxthon when I have to, and use Maxthon for a few of its features (like tabs) that I miss from Firefox.

Note about Wine vs. Crossover: I don't know if Maxthon will work under plain Wine; I suspect it will.  I decided to buy Crossover after spending hours trying to get things working under plain Wine properly.  I am a happy customer; it was definitely worth the $30 or so to have most of the apps I use "just work" rather than me spending so much time trying to tweak Wine.

---

### Post by BryanFRitt on 2007-12-14
I'm using Maxthon 1.6.3 (build 80) on Linux now!
Install IEs4Linux, 
Using IEs4Linux download and install Maxthon using IEs4Linux,
set IE's homepage to Maxthon.exe, 
(file:///c:/Program%20Files/Maxthon/maxthon.exe),
and it works!
some problems though,
Right click on page dosen't work (shows the menu and disapears),
Right click works in this text box but has a slight delay,
The back and forward buttons on the mouse don't work,
Menu's start off black, go fuzzy, and then work,
(It's only a fraction of a second delay before working)

Maxthon 2.0 installed, but didn't work beyond that for me.

---

### Post by nitePhyyre on 2008-01-17
Can anyone please help out with this?  I've just switched to Linux, and after a week of using firefox, I've come to the conclusion that Maxthon2 is the only browser worth using.  I don't know what I'll do without it.

Please, please help me :(

---

### Post by Culprit on 2008-03-28
Maxthon 2.0.9.1640 is working under Ubuntu/GG.

I need to delete mxguardian and mxwebboost modules. And run with sharing profile.
Than is Maxthon working.

But on many websites are links "death", on click at link nothing appears. Opening links in new tab on this websites is working and the website under this link is loaded into new tab.

So Maxthon is still not usefull

---

### Post by Eiríkr on 2008-03-28
> **tomviolin said:**
> I need to use IE to access one or two sites that don't work under Linux Firefox.  Rather than always having to launch VMware, I am using Crossover to run IE.  

I'm curious what websites this might refer to.  Some sites do browser sniffing simply to promote whatever browser they think their site displays better in, and will block other browsers regardless of actual website functionality.  The corporate intranet at one place I worked was like that.  It didn't take long to work around it, though, by simply changing the user agent string for Firefox to instead claim that it was IE6 (See [this Wikipedia article on user agent spoofing](http://en.wikipedia.org/wiki/User_agent#User_agent_spoofing)).  Bam, the intranet suddenly let me in, and almost everything worked as it should.  The few things that didn't, I didn't need, so all was good.  

I've looked around online to find out what this Maxthon thing is, and for the life of me, I can't tell why folks would be so hooked on it.  How much browsing do you all actually do?  Is there anything wrong with other browsers that you all seem to dislike them so much?  And given the truly disastrous track record IE has, why would you trust any browser built on it over an open-source browser?  :confused:  I'm honestly asking here, because I'd like to know what people's thoughts and opinions are.  

Curious,

Eiríkr

---

### Post by nitePhyyre on 2008-03-28
There are many many reasons Maxthon is better than anything else out there.  It has so many features that I'm sure 2 people who use it would give you different reasons for it.  So these are just some of the things I like in it.

It is very customizable, without plugins.  It does have plugins, but there are some things that you shouldn't need them for.  Needing plugins to change basic functionality is a bit absurd. It has a much smaller memory footprint.  I can easily have 100 tabs open and not even worry about my system slowing down.  (and yes, i do use that many tabs, lol)

It has a login system, so i can go to my friends house, login to my account, and have all my settings and favorites come with me.  Mouse gestures, at first i thought they were pointless, but wow, once you start using them, I feel like a cripple without them. CTRL+left/right to scroll through tabs.  Super drag and drop:  Select some text, drag it, Maxthon opens a new tab with the selected text google searched. Drag a link, it opens in a new tab.

Oh, and i had forgot what popups were till I started using firefox again.

In any case, Culprit how did you get it to work, same steps as BryanFRitt  took?

---

### Post by Eiríkr on 2008-03-28
> It is very customizable, without plugins. It does have plugins, but there are some things that you shouldn't need them for. Needing plugins to change basic functionality is a bit absurd. 

I agree in principle, but what basic functionality are you referring to?

> It has a much smaller memory footprint. I can easily have 100 tabs open and not even worry about my system slowing down.

That's good, memory bog-down is my current beef with Firefox, though I understand that's supposed to be better in v3.

> It has a login system, so i can go to my friends house, login to my account, and have all my settings and favorites come with me. 

This implies some online server somewhere storing your data, and as such seems to fall outside the bounds of a basic browser...?

> Oh, and i had forgot what popups were till I started using firefox again.

I'm on Firefox but haven't seen a popup in ages, either.  :confused:

Cheers,

Eiríkr

---

### Post by Culprit on 2008-04-02
> **nitePhyyre said:**
> In any case, Culprit how did you get it to work, same steps as BryanFRitt  took?
How? Very simple.
I'm using this version of wine```
dpkg -l| grep wine
ii  wine                                       0.9.58-0ubuntu2               Microsoft Windows Compatibility Layer (Binar
```Installation```
##############################################################
# Downloads:
##############################################################
#Maxthon 2.0.9.1640 UNICODE
wget http://www.maxthon.cz/modules/mx_pafiledb/dload.php?action=download&file_id=75
#mfc42u.zip
wget http://www.dll-files.com/dllindex/download.php?mfc42udownload0VMjOAcEhO
##############################################################
#Install
##############################################################
wine mx_2.0.9.1640.exe
unzip mfc42u.zip
cp mfc42u.dll ~/.wine/drive_c/windows/system32/
cd ~/.wine/drive_c/Program\ Files/Maxthon2/Modules/
rm MxGuardian -rfv
##############################################################
#START
##############################################################
wine ~/.wine/drive_c/Program\ Files/Maxthon2/Maxthon.exe
```:lolflag:
On First page select **Start without Account**.
Install Gecko if necessary. 
Than appears message box with sending options: Select **Cancel**.
than appears maxConfig :: INIT OBJECT FAILED and simply click OK.

Maxthon will start. Other problem you will resolve self. When link is not working drag it simply into tab bar.

---

### Post by shaian on 2008-05-01
anyone test it ?

i cant work with any other browsers :( ...

---

### Post by BryanFRitt on 2008-06-24
Got Maxthon Version 2.1.1.1717 UNICODE working on using IEs4Linux 2.99.0 and wine 1.0.  I get an error message when I start it,(via double click in konqueror ~/.ies4linux/ie6/drive_c/Program Files/Maxthon2/Maxthon.exe, Start without Account) maxStart.init :: failed to init, When I goto tools->Internet Options, nothing happens.  When I goto tools->Maxthon Setup Center, a tab will show, but it doesn't work at all, or maxConfig :: INIT OBJECT FAILED error. and the page is missing the options, and just shows the categories on the left hand side, can click on them and make the background of each one of turn blue, sometimes get error message: maxOptions.pages.---.destroy() 0 : maxOptions.pages.general.destroy is not a function. (for *page_key, *page_skin, *page_plugin, *page_filter) where --- is the text after *page_ 
basically none of the max:------ pages work.  At one point it said: "HTML rendering is currently disabled"  

Also tried installing using wine rather than explorer ie4linux to install it, still same weird results.(~/.wine/drive_c/Program Files/Maxthon2/Maxthon.exe' vs ~/.ies4linux/ie6/drive_c/Program Files/Maxthon2/Maxthon.exe) sometimes web pages were working, but sometimes not, no max: websites working, and no 'Internet Options'.

I'm using Firefox 3 with some plugins, and I am fine with it.

---

