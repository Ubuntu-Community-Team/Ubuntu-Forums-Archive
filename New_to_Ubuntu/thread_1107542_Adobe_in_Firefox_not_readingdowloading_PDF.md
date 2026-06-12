---
title: "Adobe in Firefox not reading/dowloading PDF"
date: 2009-03-26
forum: New to Ubuntu
---

### Post by dunbrokin on 2009-03-26
See attached screenshot....I was trying to download the conference programme.....I have Adobe installed....so I don't understand what the problem is. HELP!

---

### Post by dunbrokin on 2009-03-26
Ooops!

---

### Post by oldsoundguy on 2009-03-26
I use "PDF download" .. it is an add on that comes with Firefox .. it works about 10 times faster than Adobe reader with it's splash screen and credits!  Give it a shot 
(through your tools menu)

---

### Post by oldsoundguy on 2009-03-26
OH, & BTW, you need to get a cooler on that processor before it melts or it does damage to adjacent components on your motherboard.

I have a hyperthreaded that used to run that hot until I put a Cooler Master kit on it .. now it runs at 44-45C under FULL LOAD.

---

### Post by Chemical Imbalance on 2009-03-26
> **yoyomick said:**
> your attachment are too samll to read.

click on it.

---

### Post by presence1960 on 2009-03-26
> **dunbrokin said:**
> See attached screenshot....I was trying to download the conference programme.....I have Adobe installed....so I don't understand what the problem is. HELP!

Install the mozilla acroread plugin . In terminal ```
sudo apt-get install mozilla-acroread
```

---

### Post by dunbrokin on 2009-03-26
> **presence1960 said:**
> Install the mozilla acroread plugin . In terminal ```
sudo apt-get install mozilla-acroread
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  mozilla-acroread: Depends: acroread (>= 7.0) but it is not going to be installed
                    Depends: acroread-escript but it is not going to be installed
E: Broken packages

---

### Post by dunbrokin on 2009-03-26
> **oldsoundguy said:**
> OH, & BTW, you need to get a cooler on that processor before it melts or it does damage to adjacent components on your motherboard.

I have a hyperthreaded that used to run that hot until I put a Cooler Master kit on it .. now it runs at 44-45C under FULL LOAD.

Why does it run so much hotter in Ubuntu than in Windows?

---

### Post by Chemical Imbalance on 2009-03-26
do what oldsoundguy mentioned and go to add-ons in firefox, then go to the get-add-ons tab and search for pdf download.  Install that and see how that works for you.  

And I agree about your cpu.  If that is a desktop, you need better cooling solutions (a better fan and some thermal paste).

---

### Post by dunbrokin on 2009-03-26
> **Chemical Imbalance said:**
> do what oldsoundguy mentioned and go to add-ons in firefox, then go to the get-add-ons tab and search for pdf download.  Install that and see how that works for you.  

And I agree about your cpu.  If that is a desktop, you need better cooling solutions (a better fan and some thermal paste).

Already tried that....does not work....

This is a laptop.

---

### Post by oldsoundguy on 2009-03-26
> **dunbrokin said:**
> Why does it run so much hotter in Ubuntu than in Windows?

I have found in most cases the opposite to be the fact.  Linux run cooler .. BUT, as I noted, my processor(s) (7 computers right now) run at 100% all the time as I run items for BOINC computing in the background.

The best fan/HS combo I have found is the Cooler Master Aero.  Nice and quiet and it WORKS.

EDIT .. the above is for desktops ..

Google "laptop cooler"  Have several friends using same and they get some good results.

---

### Post by Chemical Imbalance on 2009-03-26
That's pretty high still for a laptop, but more tolerable.  It would be worrying if that was a desktop.

I personally just download the pdf's to my desktop and then read them.

---

### Post by Chemical Imbalance on 2009-03-26
> **oldsoundguy said:**
> I have found in most cases the opposite to be the fact.  Linux run cooler .. BUT, as I noted, my processor(s) (7 computers right now) run at 100% all the time as I run items for BOINC computing in the background.

The best fan/HS combo I have found is the Cooler Master Aero.  Nice and quiet and it WORKS.

EDIT .. the above is for desktops ..

Google "laptop cooler"  Have several friends using same and they get some good results.

He's on a laptop.

--

oops, sorry for the double post.

---

### Post by dunbrokin on 2009-03-26
> **Chemical Imbalance said:**
> That's pretty high still for a laptop, but more tolerable.  It would be worrying if that was a desktop.

I personally just download the pdf's to my desktop and then read them.

So do I....but this one will not download...see if you can get it to download.

---

### Post by presence1960 on 2009-03-26
> **dunbrokin said:**
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  mozilla-acroread: Depends: acroread (>= 7.0) but it is not going to be installed
                    Depends: acroread-escript but it is not going to be installed
E: Broken packages

Look in synaptic for acroread-plugins mozilla. I am using 64 bit Hardy and the mozilla plugin is mozilla-acroread. BTW I installed acroread (Adobe) first from synaptic then the plugin. It works flawlessly.

Note: Acroread is 8.1.3 and you need Medibuntu enabled.

---

### Post by dunbrokin on 2009-03-26
> **presence1960 said:**
> Look in synaptic for acroread-plugins mozilla. I am using 64 bit Hardy and the mozilla plugin is mozilla-acroread. BTW I installed acroread (Adobe) first from synaptic then the plugin. It works flawlessly.

acroread:
 Depends: libldap2  but it is not installable

is the message I get in Synaptic.

---

### Post by presence1960 on 2009-03-26
> **dunbrokin said:**
> acroread:
 Depends: libldap2  but it is not installable

is the message I get in Synaptic.

Sorry Dunbrokin, I had it working when I ran 8.10 but right now I can't remember the exact package name. I am pretty sure it was acroread-plugins mozilla. On Hardy I have acroread-mozilla for the firefox plugin.

---

### Post by lovinglinux on 2009-03-26
> **dunbrokin said:**
> Already tried that....does not work....

This is a laptop.

You should check the temp in the BIOS and compare with the one displayed in the panel, because those sensors can be wrong if they are not properly configured. I remember that, when I first installed them, they displayed temperatures extremely above normal working temperatures. 

Also I think with such a high temperature, the fan would be working at full power non-stop. Is this the case?

Do you have a HP/Compaq laptop? HP recently released a BIOS patch so solve issues regarding the temperature control. This problem was preventing the fan to work properly, eventually leading to damage in the motherboard or wireless components. The patch makes the fan work all the time, non-stop.

---

### Post by dunbrokin on 2009-03-27
Thanks for that a) how do I check the temp in the BIOS?
                b) It is a Dell Latitude D610

---

### Post by lovinglinux on 2009-03-27
> **dunbrokin said:**
> Thanks for that a) how do I check the temp in the BIOS?
                b) It is a Dell Latitude D610

Do you know how to enter the BIOS setup? Did you ever enter it? There is a shortcut you have to press when booting (F8, F10 or Delete, I guess). This should be specified in the screen when you are booting.

If you never entered the BIOS setup, than I recommend reading the notebook manual first and be careful. If you mess with BIOS settings you can really screw your machine.

There is usually a section in the BIOS settings that display the current temperatures and voltages. Something like "Hardware Monitor" or "Temperature monitor".

Anyways, if you never entered the BIOS setup, didn't overclocked the CPU and if the fan seems to be working properly, the system is not unstable and the computer case does not feel extremely hot, then I would say that the problem is the gnome sensor.

---

### Post by Chemical Imbalance on 2009-03-27
> **dunbrokin said:**
> So do I....but this one will not download...see if you can get it to download.

what's the link for it?

For dell laptops ( i have a d630)  just press F8 repeatedly when the DELL logo pops up

---

### Post by monkeys on 2009-04-30
Did this problem every get solved? I am running Jaunty, and all of a sudden my Reader in Firefox won't work. I've downloaded the Acroread packages, and it tells me it's up to date.

---

### Post by dunbrokin on 2009-04-30
> **monkeys said:**
> Did this problem every get solved? I am running Jaunty, and all of a sudden my Reader in Firefox won't work. I've downloaded the Acroread packages, and it tells me it's up to date.

No it never did really. Try removing acroread using symantic and reinstalling again.

---

### Post by bigoperm on 2009-05-24
I'm also having trouble reading PDFs through Firefox; not sure if the issue is related. Currently, when I click a PDF link, I get a blank screen. It's as though the acroread plugin doesn't even start. Moreover, if I go into Firefox preferences and change the behaviour to use xpdf, the problem persists.

I'm running 9.04 (Jaunty Jackalope). Here are some system specifics:
```
$> uname -a
Linux [machine-name] 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:58:03 UTC 2009 x86_64 GNU/Linux
$> sudo apt-get install acroread mozilla-acroread acroread-plugins
acroread is already the newest version.
mozilla-acroread is already the newest version.
acroread-plugins is already the newest version.
```

Any suggestions would be appreciated.

---

### Post by oldsoundguy on 2009-05-24
golly guys,  Your answer is as simple as installing PDF download into Fire Fox.          (it is in the Mozilla add-ons along with a lot of other really useful programs.)

---

### Post by lovinglinux on 2009-05-24
> **oldsoundguy said:**
> golly guys,  Your answer is as simple as installing PDF download into Fire Fox.          (it is in the Mozilla add-ons along with a lot of other really useful programs.)

[https://addons.mozilla.org/en-US/firefox/addon/636](https://addons.mozilla.org/en-US/firefox/addon/636)

---

### Post by bigoperm on 2009-05-25
> **oldsoundguy said:**
> golly guys,  Your answer is as simple as installing PDF download into Fire Fox.          (it is in the Mozilla add-ons along with a lot of other really useful programs.)
This seems like a good solution, but I'm still wondering why supposedly supported tools ("mozilla-acroread" and "acroread-plugins") aren't working...

---

### Post by sanika on 2009-07-02
Adobe Reader's latest version ia 9.1.2. You can download it from [ftp://ftp.adobe.com/pub/adobe/reader/unix/9.x/9.1.2/. ]("ftp://ftp.adobe.com/pub/adobe/reader/unix/9.x/9.1.2/")Installing Adobe Reader 9.1.2 would install the browser plugin for you. You can check it by typing about: plugins in the browser's address bar. Make sure you have the path to acroread script in your PATH variable. If you have installed reader at the default location /opt, there is no need to set PATH variable. In case you have installed it at any other location, use the following command in a terminal :

export PATH=<dir_where_acroread_is_installed/Adobe/Reader9/bin>:$PATH 

Now you can launch browser from this terminal and use Adobe Reader to open PDFs.

---

### Post by bigoperm on 2009-07-17
My most recent Intrepid "dist-upgrade" solved this problem.

---

### Post by asalapi on 2010-06-01
Well, we seem to be having a regression here. On ubuntu lucid, firefox  3.6.3 and adobe reader 9.3 plugin the problem appears again to me (in  two different computers).
I don't really fancy installing a new PDF plugin... I hope mozilla /  adobe correct this in a couple of weeks.

---

