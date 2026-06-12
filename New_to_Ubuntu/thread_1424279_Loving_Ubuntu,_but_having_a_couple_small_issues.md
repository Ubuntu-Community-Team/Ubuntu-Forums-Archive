---
title: "Loving Ubuntu, but having a couple small issues"
date: 2010-03-07
forum: New to Ubuntu
---

### Post by AComplex on 2010-03-07
First of all, I'd just like to thank everyone working on/with Ubuntu. I'm totally blown away by how much faster and more stable 9.10 is over Vista. However, I'm having a couple small issues that I want to resolve before just removing Vista partition for good.

A little context: I'm using this laptop primarily for schoolwork (Biochemistry), but I also watch a lot of movies from here and have a pretty large music library. It's my only computer and I heavily rely on it for day to day things.

1) I have Amarok and found all my old music on the harddrive. However, I can't play any music. I'm guessing it's a problem with an audio codec, but I'm not sure how to find them in Ubuntu. Sound plays fine in VLC and online (grooveshark, youtube etc.). So maybe it has something to do with the KDE wallet (I don't know what this means)

2) Is there an Alarm Clock program that will wake a computer up from suspension and play a song? Citrus Alarm Clock did this in windows and I rather use my computer instead of buying an alarm clock.

3) Is there a plug-in that gives OpenOffice easier formatting? I'm loving the simplicity of OpenOffice, but sometimes I find myself wishing I had the little formatting ribbon from Word2007.

4) I tried to install Folding@Home the Terminal using a program called Origami. But I'm unsure if it's actually functioning. Also, I remember there being a screensaver you could get to show your progress. Does that work in Ubuntu?

5) I'm still looking around, but are there any programs you consider essential but doesn't come with the original suite? All I have so far is VLC, Wine, KTorrent and Amarok and I'm sure there's a ton of stuff I'm overlooking.

Sorry if any of this is old news. I appreciate the community here and would like to thank guys again for making my computer experience pleasant again.

---

### Post by steindor2 on 2010-03-07
> **AComplex said:**
> 

1) I have Amarok and found all my old music on the harddrive. However, I can't play any music. I'm guessing it's a problem with an audio codec, but I'm not sure how to find them in Ubuntu. Sound plays fine in VLC and online (grooveshark, youtube etc.). So maybe it has something to do with the KDE wallet (I don't know what this means)

paste this into your terminal
```
sudo apt-get install ubuntu-restrictred-extras
```

4) I tried to install Folding@Home the Terminal using a program called Origami. But I'm unsure if it's actually functioning. Also, I remember there being a screensaver you could get to show your progress. Does that work in Ubuntu?

probably not

5) I'm still looking around, but are there any programs you consider essential but doesn't come with the original suite? All I have so far is VLC, Wine, KTorrent and Amarok and I'm sure there's a ton of stuff I'm overlooking.

Deluge
google chrome
Catfish

[COLOR=White]a[/COLOR]
[COLOR=White]b[/COLOR]

---

### Post by AComplex on 2010-03-07
> **steindor2 said:**
> [COLOR=White]a[/COLOR]
[COLOR=White]b[/COLOR]

Heh, this shows just how new I am to this, but how do you acknowledge the User Conditions in Terminal. I have a big block of text and an <OK> at the bottom, but neither space nor enter seem to do anything.

---

### Post by Neezer on 2010-03-07
> **AComplex said:**
> Heh, this shows just how new I am to this, but how do you acknowledge the User Conditions in Terminal. I have a big block of text and an <OK> at the bottom, but neither space nor enter seem to do anything.

You need to use the arrow keys and then hit enter when the ok is hilighted

---

### Post by Rasa1111 on 2010-03-07
Hi and Welcome, 

Maybe also install "Deja Dup" ~ it is a backup utility. 
 I have installed at least 3 other ones before this , and none of them impressed me much. 

Deja Dup works great for backing up your system and saving it for later use. 

yeah the "Ubuntu Restricted Extras" should take care of your missing codecs also. 

im a newb so I havent much help to offer,  but that should help a little i think, for something at least. lol  <3

good luck.

---

### Post by peace.gangsta on 2010-03-07
I am looking forward to the alarm clock question you raised ..I still haven't found any such software on my only Linux world.

---

### Post by AComplex on 2010-03-07
Alright, I think I might have messed something up. I canceled the Ubuntu Restricted Extras installation from terminal to try it through the Software Centre. However, I'm getting this message (after a restart)

E:I wasn't able to locate a file for the sun-java6-jre package. This might mean you need to manually fix this package. (due to missing arch):

---

### Post by jmszr on 2010-03-07
AComplex,

This Comprehensive Multimedia and Video Howto should take care of any video issues: [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683) .

I would add k3b for CD burning.

About Folding@Home, perhaps the Ubuntu Team can help you: [http://ubuntuforums.org/showthread.php?t=102313](http://ubuntuforums.org/showthread.php?t=102313) or: [https://wiki.ubuntu.com/FoldingAtHomeTeamUbuntu](https://wiki.ubuntu.com/FoldingAtHomeTeamUbuntu)

---

### Post by Kaligo on 2010-03-07
You might want to try [HTML]sudo aptitude reinstall ubuntu-restricted-extras[/HTML] which should clear up any problems from cancelling halfway through an installation.

For the alarm clock, you can schedule almost any action using cron but I suspect there would be a much simpler application out there for what you want to do.

---

### Post by AComplex on 2010-03-07
> **Kaligo said:**
> You might want to try [HTML]sudo aptitude reinstall ubuntu-restricted-extras[/HTML] which should clear up any problems from cancelling halfway through an installation.

For the alarm clock, you can schedule almost any action using cron but I suspect there would be a much simpler application out there for what you want to do.

Heh, I figured out through Synaptic. But thank you for the advice. I'm going to work with cron right now.

---

### Post by Kaligo on 2010-03-07
After searching for "alarm" in the Ubuntu Software Centre a couple of results came up, I assume you're using Kubuntu from the other software mentioned.  Have you tried KAlarm?

---

### Post by egalvan on 2010-03-07
Are you using Kubuntu or Ubuntu?

you may have to adjust the restricted extras if you are running Kubuntu.

Personally, I have both installed (KDE and Gnome) and installed both extras packages.

Also, *jmszr* (post #8) has some excellent tips, be sure to follow them.

Again, be aware of the differences between KDE (Kubuntu) and Gnome (Ubuntu).

---

### Post by AComplex on 2010-03-07
> **Kaligo said:**
> After searching for "alarm" in the Ubuntu Software Centre a couple of results came up, I assume you're using Kubuntu from the other software mentioned.  Have you tried KAlarm?

Actually I'm using the plain Ubuntu, but I don't really understand the difference between the two.

EDIT: Banshee seems to work for music. Problem solved, I think.

---

### Post by egalvan on 2010-03-07
As for an alarm clock...

install...
Quod Libet

then get these...
quodlibet-plugins

which has this...
* - Alarm clock and lullaby, start and stop playing music at specified times*


n.b. Quod Libet is a media player.
Found in Synaptic.

---

### Post by m4tic on 2010-03-07
i haven't touched my ubuntu partition in a whole month since installing mandriva one. feels solid

---

### Post by AComplex on 2010-03-07
Another problem I'm having, my wireless seems way stronger with Windows. It keeps on cutting out. I had to switch back to Vista to post this. :(

---

### Post by puzzler995 on 2010-03-07
> **AComplex said:**
> Another problem I'm having, my wireless seems way stronger with Windows. It keeps on cutting out. I had to switch back to Vista to post this. :(
That may be a problem with your wireless card. what model do you have, if you know...

---

### Post by AComplex on 2010-03-07
> **puzzler995 said:**
> That may be a problem with your wireless card. what model do you have, if you know...

Atheros AR9281 Wireless Network Adapter
Realtek RTL8102E/8103E Family PCI-E Fast Ethernet NIC (NDIS 6.0)

---

### Post by AComplex on 2010-03-08
bump

---

### Post by egalvan on 2010-03-10
> **AComplex said:**
> Atheros AR9281 Wireless Network Adapter
Realtek RTL8102E/8103E Family PCI-E Fast Ethernet NIC (NDIS 6.0)

I suggest starting a new thread with *Realtek RTL8102E/8103E* in the title.

---

### Post by oingk on 2010-03-10
> **AComplex said:**
> 
3) Is there a plug-in that gives OpenOffice easier formatting? I'm loving the simplicity of OpenOffice, but sometimes I find myself wishing I had the little formatting ribbon from Word2007.
What do you mean by "formatting", if you don't mind me asking?

---

### Post by oingk on 2010-03-10
Because if you mean what MS Word has here: [http://regnow.img.digitalriver.com/vendor/22601/Shot_Menu_Word_800_600.jpg](http://regnow.img.digitalriver.com/vendor/22601/Shot_Menu_Word_800_600.jpg)

Then you can do all these things by clicking "Format" on the toolbar, like here:
[http://media.overnightprints.com/img1/en/specs/openoffice/v001_OpenOffice_pageFormat.gif](http://media.overnightprints.com/img1/en/specs/openoffice/v001_OpenOffice_pageFormat.gif)

Just the names of things might be a bit different

---

