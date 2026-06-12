---
title: "Java Plug-in not detected"
date: 2009-10-18
forum: New to Ubuntu
---

### Post by CSHANKY on 2009-10-18
Would appreciate [COLOR=Green]step-by-step instructions[/COLOR], appropriate for a newbie non-software 
literate person to resolve this issue, that's driving me nuts, as I cannot log-in to my company website, which requires it to be able to detect Flash. (I keep getting "[COLOR=blue]Flash detection in progress...please wait...")[/COLOR]
[COLOR=Green]Thanks.[/COLOR]

----------

_**Problem**_
Firefox Plugin Check says -
Java(TM) Plug-in 1.6.0_16: [COLOR=Red]Unable[/COLOR] to Detect Plugin Version

**[COLOR=Magenta]Having problems running some applications as a result of the above[/COLOR]**

Data:

Firefox Version: Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.1.3)Gecko/20090824 Firefox/3.5.3

Tests performed:

[www.java.com]("http://www.java.com")
Verified Java Version
[COLOR=Green]Congratulations! You have the recommended Java installed (Version 6 Update 16).[/COLOR]

Java Plug-in 1.6.0_16
[COLOR=Green]Using JRE version 1.6.0_16-b01 Java HotSpot(TM) Client VM
[/COLOR]
Shockwave Flash 10.0 r32 installed

Ubuntu:[COLOR=Green] 9.04 installed
[/COLOR]

---

### Post by sync on 2009-10-18
in the terminal, try typing 'sudo apt-get install adobe-flashplugin'
Let me know how that goes for you.

---

### Post by CSHANKY on 2009-10-18
~$ sudo apt-get install adobe-flashplugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
adobe-flashplugin is already the newest version.
**0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.**

---

### Post by broken_arrow on 2009-10-18
I have the same issue and ran apt-get install adobe-flashplugin and received the following response the my terminal window:

adobe-flashplugin is already the newest version.
The following packages were automatically installed and are no longer required:
  libao2
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.

---

### Post by sync on 2009-10-18
try 'sudo apt-get install flashplugin-installer'

---

### Post by QIII on 2009-10-18
Open Firefox.
  
  In the navigation bar, type in about (colon) plugins.  That is "about" followed by a colon, followed by "plugins"
  
  Tell us if you see the Java plugin listed.

You may also have to make sure that the flash plugin is in the right folder, etc.  But let me know what you find out with the above first.

---

### Post by CSHANKY on 2009-10-18
**Installed plugins**

 Find more information about browser plugins at  [mozilla.org]("https://pfs.mozilla.org/plugins/"). 
 Help for installing plugins is available from  [plugindoc.mozdev.org]("http://plugindoc.mozdev.org/"). 
 **Default Plugin**

 File name:  libnullplugin.so The default plugin handles plugin data for mimetypes and extensions that are not specified and facilitates downloading of new plugins.   MIME Type Description Suffixes Enabled    * All types .* No  **Shockwave Flash**

 File name:  libflashplayer.so Shockwave Flash 10.0 r32   MIME Type Description Suffixes Enabled    application/x-shockwave-flash Shockwave Flash swf Yes   application/futuresplash FutureSplash Player spl Yes  **Java(TM) Plug-in 1.6.0_16**

 File name:  libnpjp2.so The next generation [Java]("http://java.sun.com/") plug-in for Mozilla browsers.   MIME Type Description Suffixes Enabled    application/x-java-vm Java™ Plug-in 
Yes   application/x-java-applet Java™ Plug-in Applet 
Yes   application/x-java-applet;version=1.1 Java™ Plug-in 
Yes   application/x-java-applet;version=1.1.1 Java™ Plug-in 
Yes   application/x-java-applet;version=1.1.2 Java™ Plug-in 
Yes   application/x-java-applet;version=1.1.3 Java™ Plug-in 
Yes   application/x-java-applet;version=1.2 Java™ Plug-in 
Yes   application/x-java-applet;version=1.2.1 Java™ Plug-in 
Yes   application/x-java-applet;version=1.2.2 Java™ Plug-in 
Yes   application/x-java-applet;version=1.3 Java™ Plug-in 
Yes   application/x-java-applet;version=1.3.1 Java™ Plug-in 
Yes   application/x-java-applet;version=1.4 Java™ Plug-in 
Yes   application/x-java-applet;version=1.4.1 Java™ Plug-in 
Yes   application/x-java-applet;version=1.4.2 Java™ Plug-in 
Yes   application/x-java-applet;version=1.5 Java™ Plug-in 
Yes   application/x-java-applet;version=1.6 Java™ Plug-in 
Yes   application/x-java-applet;jpi-version=1.6.0_16 Java™ Plug-in 
Yes   application/x-java-bean Java™ Plug-in JavaBeans 
Yes   application/x-java-bean;version=1.1 Java™ Plug-in 
Yes   application/x-java-bean;version=1.1.1 Java™ Plug-in 
Yes   application/x-java-bean;version=1.1.2 Java™ Plug-in 
Yes   application/x-java-bean;version=1.1.3 Java™ Plug-in 
Yes   application/x-java-bean;version=1.2 Java™ Plug-in 
Yes   application/x-java-bean;version=1.2.1 Java™ Plug-in 
Yes   application/x-java-bean;version=1.2.2 Java™ Plug-in 
Yes   application/x-java-bean;version=1.3 Java™ Plug-in 
Yes   application/x-java-bean;version=1.3.1 Java™ Plug-in 
Yes   application/x-java-bean;version=1.4 Java™ Plug-in 
Yes   application/x-java-bean;version=1.4.1 Java™ Plug-in 
Yes   application/x-java-bean;version=1.4.2 Java™ Plug-in 
Yes   application/x-java-bean;version=1.5 Java™ Plug-in 
Yes   application/x-java-bean;version=1.6 Java™ Plug-in 
Yes   application/x-java-bean;jpi-version=1.6.0_16 Java™ Plug-in 
Yes  **DivX® Web Player**

 File name:  libtotem-mully-plugin.so DivX Web Player version 1.4.0.233   MIME Type Description Suffixes Enabled    video/divx AVI video divx Yes  **QuickTime Plug-in 7.2.0**

 File name:  libtotem-narrowspace-plugin.so The [Totem]("http://www.gnome.org/projects/totem/") 2.26.1 plugin handles video and audio streams.   MIME Type Description Suffixes Enabled    video/quicktime QuickTime video mov Yes   video/mp4 MPEG-4 video mp4 Yes   image/x-macpaint MacPaint Bitmap image pntg Yes   image/x-quicktime Macintosh Quickdraw/PICT drawing pict, pict1, pict2 Yes   video/x-m4v MPEG-4 video m4v Yes  **VLC Multimedia Plugin (compatible Totem 2.26.1)**

 File name:  libtotem-cone-plugin.so The [Totem]("http://www.gnome.org/projects/totem/") 2.26.1 plugin handles video and audio streams.   MIME Type Description Suffixes Enabled    application/x-vlc-plugin VLC Multimedia Plugin 
Yes   application/vlc VLC Multimedia Plugin 
Yes   video/x-google-vlc-plugin VLC Multimedia Plugin 
Yes   application/x-ogg Ogg multimedia file ogg Yes   application/ogg Ogg multimedia file ogg Yes   audio/ogg Ogg Audio oga Yes   audio/x-ogg Ogg Audio ogg Yes   video/ogg Ogg Video ogv Yes   video/x-ogg Ogg Video ogg Yes   application/annodex Annodex exchange format anx Yes   audio/annodex Annodex Audio axa Yes   video/annodex Annodex Video axv Yes   video/mpeg MPEG video mpg, mpeg, mpe Yes   audio/wav WAV audio wav Yes   audio/x-wav WAV audio wav Yes   audio/mpeg MP3 audio mp3 Yes   application/x-nsv-vp3-mp3 NullSoft video nsv Yes   video/flv Flash video flv Yes   application/x-totem-plugin Totem Multimedia plugin 
Yes  **Windows Media Player Plug-in 10 (compatible; Totem)**

 File name:  libtotem-gmp-plugin.so The [Totem]("http://www.gnome.org/projects/totem/") 2.26.1 plugin handles video and audio streams.   MIME Type Description Suffixes Enabled    application/x-mplayer2 AVI video avi, wma, wmv Yes   video/x-ms-asf-plugin ASF video asf, wmv Yes   video/x-msvideo AVI video asf, wmv Yes   video/x-ms-asf ASF video asf Yes   video/x-ms-wmv Windows Media video wmv Yes   video/x-wmv Windows Media video wmv Yes   video/x-ms-wvx Windows Media video wmv Yes   video/x-ms-wm Windows Media video wmv Yes   video/x-ms-wmp Windows Media video wmv Yes   application/x-ms-wms Windows Media video wms Yes   application/x-ms-wmp Windows Media video wmp Yes   application/asx Microsoft ASX playlist asx Yes   audio/x-ms-wma Windows Media audio wma Yes

---

### Post by QIII on 2009-10-18
Go to the terminal and type 

```
java -version
```

---

### Post by CSHANKY on 2009-10-18
java version "1.6.0_16"
Java(TM) SE Runtime Environment (build 1.6.0_16-b01)
Java HotSpot(TM) Client VM (build 14.2-b01, mixed mode, sharing)

---

### Post by QIII on 2009-10-18
Are you able to see Flash content on other sites like YouTube?

Using Synaptic, can you tell me if you have swfdec or gnash installed?

They will show up if you search for "flash".

These two cause conflicts with Flash.

---

### Post by beastrace91 on 2009-10-18
> **CSHANKY said:**
> 
Tests performed:

[www.java.com]("http://www.java.com")
Verified Java Version
[COLOR=Green]Congratulations! You have the recommended Java installed (Version 6 Update 16).[/COLOR]

Java Plug-in 1.6.0_16
[COLOR=Green]Using JRE version 1.6.0_16-b01 Java HotSpot(TM) Client VM
[/COLOR]
Shockwave Flash 10.0 r32 installed

Ubuntu:[COLOR=Green] 9.04 installed
[/COLOR]

If those tests come up A-Ok then your plugins are working and installed just fine - sounds like an incompatibility issue with your company's website. Try installing firefox+java+flash through Wine and give that a go. Some sites just hate Linux :(

~Jeff

---

### Post by CSHANKY on 2009-10-18
Are you able to see Flash content on other sites like YouTube?
[COLOR=Red]- Yes[/COLOR]


Using Synaptic, can you tell me if you have swfdec or gnash installed?

I see: 
[COLOR=Red]swfdec-gnome
swfdec-mozilla

gnash
gnash-cygnal
gnash-tool[/COLOR]

---

### Post by beastrace91 on 2009-10-18
> **CSHANKY said:**
> 
_**Problem**_
Firefox Plugin Check says -
Java(TM) Plug-in 1.6.0_16: [COLOR=Red]Unable[/COLOR] to Detect Plugin Version

He is having a Java issue - not a flash issue... >.<

~Jeff

---

### Post by CSHANKY on 2009-10-18
Thanks....I used to able to access my co site fine with Ubuntu 9.04 for ~1.5 months, until the darn thing froze up for no reason whatsoever two days back.

So I reinstalled Ubuntu...and have been struggling ever since.... 

Extremely frustrating....Ubuntu has L-O-O-O-O-N-G ways to go to able to offer any serious competition to MS, IMHO.

But hey, it's free! And works...most of the time.

---

### Post by QIII on 2009-10-18
Are swfdec and gnash marked as installed?

If so, mark them for removal and remove them.

In FF, under Edit | Preferences | Content do you have "Enable JavaScript" checked.

---

### Post by beastrace91 on 2009-10-18
> **CSHANKY said:**
> Extremely frustrating....Ubuntu has L-O-O-O-O-N-G ways to go to able to offer any serious competition to MS, IMHO.

The issue you are having is regarding a lack of support for Linux is either your sites fault or Javas... Not really Ubuntu/Linux's fault.

~Jeff

---

### Post by QIII on 2009-10-18
> **beastrace91 said:**
> He is having a Java issue - not a flash issue... >.<

~Jeff
  
Not necessarily.  He has the latest version of Java installed and it is showing up under java -version.

What he sees may be a red herring, which is why it is important to troubleshoot rather than making quick judgments.

---

### Post by CSHANKY on 2009-10-18
Are swfdec and gnash marked as installed?

None of these are checked.
[COLOR=Red]swfdec-gnome
swfdec-mozilla
 gnash
gnash-cygnal
gnash-tool

[/COLOR]In FF, under Edit | Preferences | Content do you have "Enable JavaScript" checked.
[COLOR=Red]Ye[/COLOR]s

---

### Post by QIII on 2009-10-18
Which version of FF are you using?

---

### Post by CSHANKY on 2009-10-18
> **beastrace91 said:**
> The issue you are having is regarding a lack of support for Linux is either your sites fault or Javas... Not really Ubuntu/Linux's fault.

~Jeff
:-) typical response, as expected...but thanks anyways! :)

---

### Post by CSHANKY on 2009-10-18
> **QIII said:**
> Which version of FF are you using?
Firefox Version: Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.1.3)Gecko/20090824 Firefox/3.5.3

---

### Post by QIII on 2009-10-18
> **CSHANKY said:**
> Ttypical response, as expected...but thanks anyways!

It is, unfortunately, a fact that Linux is often not supported.  An example would be hardware manufacturers who don't wite Linux drivers for their hardware.

But your issue here is different.  If you were able to access your company website before, then you should be able to now.

We need to find out what changed.

---

### Post by QIII on 2009-10-18
Your original post said

> 
_**Problem**_
Firefox Plugin Check says -
Java(TM) Plug-in 1.6.0_16: [COLOR=Red]Unable[/COLOR] to Detect Plugin Version

Is that being returned by the website?

Also:  Are you still using Jaunty, or did you install Karmic this time?

---

### Post by CSHANKY on 2009-10-18
> **QIII said:**
> Your original post said



Is that being returned by the website?

Also:  Are you still using Jaunty, or did you install Karmic this time?
Yes....these are copied/pasted from:
[http://www.mozilla.com/en-US/plugincheck/](http://www.mozilla.com/en-US/plugincheck/)

---

### Post by CSHANKY on 2009-10-18
> **CSHANKY said:**
> Yes....these are copied/pasted from:
[http://www.mozilla.com/en-US/plugincheck/](http://www.mozilla.com/en-US/plugincheck/)
and I think I am still on Jaunty....since I used my old CD to reinstall.

---

### Post by QIII on 2009-10-18
OK.

Is it possible your company website is looking for an older version of Java?  You are running Update 16.  I would *think *there wouldn't be any backwards compatibility issues as far as Java itself is concerned, but I don't know how the company website is written.

Did you have Update 13 (which I think came with Jaunty before) running when you were able to access the site?  Did you update to Update 16 this time?

(I'm on my Solaris machine right now.  Give me a couple of minutes to fire up a Jaunty machine.)

---

### Post by CSHANKY on 2009-10-18
> **QIII said:**
> OK.

Did you have Update 13 (which I think came with Jaunty before) running when you were able to access the site?  Did you update to Update 16 this time?


Unable to confirm..the first time I struggled too and installed a bunch of stuff, who knows what, and it finally worked...just followed instructions.

Thanks for your help & patience.

---

### Post by beastrace91 on 2009-10-18
> **beastrace91 said:**
> Try installing firefox+java+flash through Wine and give that a go. Some sites just hate Linux :(

Did you give this a try? It works in almost every case I have had of a website not working well under Ubuntu...

~Jeff

---

### Post by CSHANKY on 2009-10-18
> **beastrace91 said:**
> Did you give this a try? It works in almost every case I have had of a website not working well under Ubuntu...

~Jeff

I'd love to...but I really don't know how to go about it.

Install Wine....then install the MS version of Firefox etc. ?

---

### Post by beastrace91 on 2009-10-18
Yep. Open terminal and then run the following commands:

```
sudo apt-get install wine
wget http://www.kegel.com/wine/winetricks
sh winetricks firefox allfonts flash shockwave
```

This will install Wine, then the Windows version of Firefox, flash, and shockwave for you.

~Jeff

---

### Post by beastrace91 on 2009-10-18
Then to install Java for the Windows firefox download [this file](http://javadl.sun.com/webapps/download/AutoDL?BundleId=33889) and once it finishes downloading right click on it and select "run with wine"

~Jeff

---

### Post by CSHANKY on 2009-10-18
> **beastrace91 said:**
> Yep. Open terminal and then run the following commands:

```
sudo apt-get install wine
wget http://www.kegel.com/wine/winetricks
sh winetricks firefox allfonts flash shockwave
```This will install Wine, then the Windows version of Firefox, flash, and shockwave for you.

~Jeff

Thanks...will try and revert.

But the basic issue of the plugin not being detected remains unresolved. 

i.e. Firefox Plugin check says:
Java(TM) Plug-in 1.6.0_16: [COLOR=Red]Unable[/COLOR] to Detect Plugin Version

This has nothing to with my company website. I think, and I am no expert, if this fixed, the other issues will go away.

---

### Post by beastrace91 on 2009-10-18
Does Java work for you on other websites? If it is passing the Java test I am inclined to believe so but can you double check please?...

~Jeff

---

### Post by CSHANKY on 2009-10-18
And how do I do that?

---

### Post by beastrace91 on 2009-10-18
Just go to any site that is powered by java, if you need one just go to [Geogebra](http://javadl.sun.com/webapps/download/AutoDL?BundleId=33889) and select "web start" and then "web start" again. Then it will launch the Geogebra program (that runs in Java) from their website - if this works then your Java is installed and working and it is indeed a issue with your other webpage.

~Jeff

---

### Post by QIII on 2009-10-18
I don't know that he needs to go through that.

I just went to the site he got his results from and got the same message he did for the Java Plug In -- for me Update 16.

Since I develop in Java, I am relatively sure that Java is working on my Jaunty machine.

(Sorry to the OP for the long response time.  A 2 year old pre-empted you.)

Flash is working as demonstrated by YouTube.

Java can be tested by going here:  [http://java.com/en/download/help/testvm.xml](http://java.com/en/download/help/testvm.xml)

---

### Post by CSHANKY on 2009-10-18
> **QIII said:**
> I don't know that he needs to go through that.

I just went to the site he got his results from and got the same message he did for the Java Plug In -- for me Update 16.

Since I develop in Java, I am relatively sure that Java is working on my Jaunty machine.

(Sorry to the OP for the long response time.  A 2 year old pre-empted you.)

Flash is working as demonstrated by YouTube.

Java can be tested by going here:  [http://java.com/en/download/help/testvm.xml](http://java.com/en/download/help/testvm.xml)

Yes - Java is alive and working. So I guess it must be the company website... let me try the Wine option.
[IMG]file:///tmp/moz-screenshot.png[/IMG][IMG]file:///tmp/moz-screenshot-1.png[/IMG]

---

### Post by CSHANKY on 2009-10-18
> **CSHANKY said:**
> Thanks...will try and revert.

But the basic issue of the plugin not being detected remains unresolved. 

i.e. Firefox Plugin check says:
Java(TM) Plug-in 1.6.0_16: [COLOR=Red]Unable[/COLOR] to Detect Plugin Version

This has nothing to with my company website. I think, and I am no expert, if this fixed, the other issues will go away.


[COLOR=Red][SIZE=3]Ok...so I went ahead and installed Wine, Java, Flash et al.[/SIZE]
[/COLOR]
Could Log-in via the Wine setup...however application does not initiate.

Checked using the link provided:   [http://java.com/en/download/help/testvm.xml](http://java.com/en/download/help/testvm.xml)

RESULT:

SYMPTOMS 	     	    
	    
	 	 	     	     	        	 			[COLOR=Red]Applets do not run. 			[/COLOR] 	         		 		 	     	     	    	      	 	 	     	 	     	    CAUSE 	     	    
	    
	 	 	     	     	        	 			Java is not enabled in the web browser. If Java is already installed but applets do not work, you may need to enable Java through your web browser. 			

Went through:

Other Web Browsers 			 	         		 		 	     	     	 	     	     	        	 			**Firefox 0.8 and Up** 
[LIST=1]
[*]Start Mozilla Firefox browser or restart it if it is already running.
[*]Select **Tools** > **Options**.
[*]Dialog box: Options
[*]Click **Web Features** > Select **Enable Java - [COLOR=Red]Yes it is enabled ![/COLOR]**
[/LIST]

[COLOR=Red][SIZE=4]Man....I am at my wits end.[/SIZE]
[/COLOR]

---

### Post by QIII on 2009-10-18
So:

1.  In Ubuntu:  Flash is installed and working properly.  Java is installed and working properly.

2.  Through Wine:  Flash is installed and working properly.  Java is installed and not working properly.

Is that right?

---

### Post by CSHANKY on 2009-10-19
> **QIII said:**
> So:

1.  In Ubuntu:  Flash is installed and working properly.  Java is installed and working properly.

2.  Through Wine:  Flash is installed and working properly.  Java is installed and not working properly.

Is that right?

Yes :confused:

---

### Post by CSHANKY on 2009-10-19
Latest screen-shot from [www.firefox.com]("http://www.firefox.com"), plugin detection (Wine Installation)

[COLOR=Red]Java Deployment Toolkit 6.0.160.1 - Unable to detect plugin version[/COLOR]

See screenshot

This is insane......

---

### Post by beastrace91 on 2009-10-19
Try upgrading your Wine version using the instructions [here](http://www.winehq.org/download/deb) and see if that fixes the issue for Windows firefox. Java is listed as platinum for Wine .24 so it *should* still work as such in .31 (the current latest)

Also worst case scenario if you have a Windows license you could also always boot a VM to view your work's web page (this way you can avoid dual booting). This is what I have to do for my TI & blackberry software.

~Jeff

---

### Post by mivo on 2009-10-19
> **beastrace91 said:**
> Also worst case scenario if you have a Windows license you could also always boot a VM to view your work's web page (this way you can avoid dual booting). This is what I have to do for my TI & blackberry software.

No, the worst case scenario is that you decide that Linux isn't ready yet (reasons being irrelevant, just looking at results not at reasons) and that the time investment for "dealing with issues" is too large. I switched my desktop back to Windows because of Java issues, and some other work related reasons, and while it sure feels limited, there is no tweaking required, no compromises to be made (as far as essentials are concerned).

I enjoy tweaking and tinkering, so my secondary desktop and my old laptop both run Linux. I do feel it is the basically better OS, and certainly agree with the philosophy. But the machine that ensures my income must work fully and not unexpectedly break as far as very basic stuff is concerned (Java, Skype, Flash, video drivers, etc.). This happened repeatedly, and while most of it was fixable, it started to feel "too much". (My netbook, which is basically my primary portable, also runs Windows.)

Like I said, it's not a matter of blame. I know where that lies.

---

### Post by QIII on 2009-10-19
> **mivo said:**
> No, the worst case scenario is that you decide that Linux isn't ready yet ...

There are Windows forums where people seek help for the very same sorts of issues.

It is easy to assume that something is "not ready yet" when there are forums where people air their grievances.  But nobody comes to a forum seeking answers to problems they are not having.

If Linux isn't ready yet, then by the same measure neither is Windows.  People have problems with both OSs.

I have had exactly zero problems with Java or Flash.  I develop in Java on a Jaunty machine.

Both OSs can be improved by finding the source of these sorts of problems -- without giving up either -- and getting the problems properly reported.

There is nothing wrong with Windows (other than my disdain for Microsoft's business practices), nor with Linux.

The only "problem" I have encountered with Linux is the fact that vendors of software and hardware do not produce software or drivers that work well with Linux.  That doesn't mean that Linux itself is "not ready yet."

Windows works well for the vast majority of its users, as does Linux.  Each has its share of problems and each has its share of particular issues in particular installations.

If either is not appealing to a particular user, then there is no problem using the other.

But neither improves if nobody determines what lies at the source of issues encountered.

---

### Post by CSHANKY on 2009-10-20
Tried every trick suggested to the T...the only thing left for me to do is to do a headstand and stick a finger up my a**... and see if that works, I guess. If that doesn't then I guess we can blame the Hardware, 'coz  Ubuntu is beyond reproach.[IMG]http://ubuntuforums.org/images/icons/icon14.gif[/IMG]

On a serious note, Ubuntu, IMHO after 3 months of extensive use, isn't quite ready for prime-time. If your employment depends upon being able to work seamlessly with different apps, it'd be unwise to stay rely on it. e.g. a perfectly working installation just froze up for no rhyme or reason...and as with this Java issue, no one could come up with a fix. 

Good for hobbyists and tinkering around  - not for serious work.

Just my 1.5 cents...

Thanks for all your help everyone....over and out ! (for now).

---

### Post by CSHANKY on 2009-10-20
> **beastrace91 said:**
> Try upgrading your Wine version using the instructions [here]("http://www.winehq.org/download/deb") and see if that fixes the issue for Windows firefox. Java is listed as platinum for Wine .24 so it *should* still work as such in .31 (the current latest)

Also worst case scenario if you have a Windows license you could also always boot a VM to view your work's web page (this way you can avoid dual booting). This is what I have to do for my TI & blackberry software.

~Jeff


I do have a Windows License...how can I boot a VM?

---

### Post by QIII on 2009-10-20
I'm not an Ubuntu evangelist, but I will say this:

I've been using Ubuntu for 5 1/2 years.  My only complaint thus far has been lack of driver support from hardware OEMs.  That applies to all Linux distros.  I started the computer gig back in the days of punch cards, chad and acoustical coupling devices.  In my experience, *nix systems, including Linux have been far and away more stable -- except, perhaps, in the bad old days when we used to have to compile our own kernels.

I'd like to say that Windows has never crashed on me and never required a complete reinstallation.   I'd like to say that everything has worked swimmingly.  I'd like to say I've never had problems with things like Java, FF plugins, IE, Office, Visual Studio, .NET, SQL Server...

But that isn't true.

My primary income is based in the Blue world.  Even in Windows world you have to consistently and religiously back up your work and files for just that reason.

My situation my be unusual, but I've never had the same occur in Linux -- where I make a secondary income.

OpenSolaris has puked on me more than once.

Neither Windows nor Linux is perfect.  There are Windows help forums aplenty.  There are Mac forums and OpenSolaris forums.

If Windows is better for you, then nobody has any right to have any hard feelings about you using it.  Use what works for you.

---

### Post by zooounds on 2010-03-24
I have the same problem.

My Java plugins isn't detected. I'm using 9.10 with latest of everything.

---

