---
title: "I want to be Windows-free but ONE website is stopping me."
date: 2010-12-04
forum: New to Ubuntu
---

### Post by goog64 on 2010-12-04
I love Ubuntu 10.04, and I want to be free from Windows, but I cannot log in to my stock trading site with Ubuntu. I get an error message
**Java needs to be installed/upgraded**

I have the latest Java installed. Javatester.org confirms that it is working and I have visited many websites that require Java and they all work fine except this one stock trading site.
Their help desk only supports Windows, so you guys/gals are my only hope. Any ideas?

---

### Post by MooPi on 2010-12-04
Start your browser from terminal and check for errors when you log onto your stock trading site. Which version of java and which browser ? If your using Firefox the "User Agent Switcher" extension may help as well

---

### Post by rmockler on 2010-12-04
Are you using Sun Java or OpenjDk?

---

### Post by timzigg on 2010-12-04
These sorts of things are such a pain. I'm an absolute newbie but I'd suggest trying another browser, probably google chrome assuming you're using firefox.

If you manage to get on the site please write to the management and suggest they make it more gnu/linux friendly and let them know how great it is.

I wanted to make the change ages ago but I wanted to use a program called "guitar pro" which worked really badly with wine and play games which needed windows. Now the latest version of guitar pro is native to Ubuntu and I'm quitting games and getting a life :)

---

### Post by NCLI on 2010-12-04
> **goog64 said:**
> I love Ubuntu 10.04, and I want to be free from Windows, but I cannot log in to my stock trading site with Ubuntu. I get an error message
**Java needs to be installed/upgraded**

I have the latest Java installed. Javatester.org confirms that it is working and I have visited many websites that require Java and they all work fine except this one stock trading site.
Their help desk only supports Windows, so you guys/gals are my only hope. Any ideas?
Here is the solution:

1. Go to System->Administration->Software Sources
2. Find and enable the "Ubuntu partner" repository. It's in the "Other Software" tab.
3. Run an update.
4. Open the software center, and install the Sun Java 6 plugin.

---

### Post by the.phantom on 2010-12-04
in firefox address bar
type


```
about:plugins
```


look through the list and see what version and brand of java you have installed

---

### Post by asmoore82 on 2010-12-04
Aha!! One of the most overlooked solutions:
Firefox runs great in Wine!

(looks terrible, runs great)

I always keep a wine container around with Firefox/flash/shockwave/java.
I use it about once every other month.

---

### Post by TBABill on 2010-12-04
I believe Ubuntu installs the icedtea plugin for java as default. If you install sun java plugin you should be able to do whatever you need with Java online. I'm not sure whether you can leave the ice tea plugin or need to uninstall it. Just go into Synaptic and install sun java plugin (possibly called sun-java6-plugin or something close).

---

### Post by goog64 on 2010-12-05
x

---

### Post by kingbilly on 2010-12-05
A VM would be a great solution, you could remove your dual boot.  For your current problem it will be fine, but keep in mind that a virtual machine won't give you 100% of the performance you got by booting vista.  So down the road if you want to run intense software or games you may want your dual boot back.

It is also possible you need a different java version.  From my experience (and some others who helped me) the open source version would not work with Yahoo Games, specifically pool.  The solution was to install the non-free version.  I don't remember if it was from a repository or from Sun's website.

---

### Post by goog64 on 2010-12-05
Thanks for your replies, everyone. 
I have the latest SUN Java 1.6.0_22 installed (as per NCLI's method)
The IcedTea and JDK are removed to avoid conflicts.

I tried running Firefox with Wine 1.2 but got the same error message about Java. (Wine wouldn't open Internet Explorer so I couldn't try that.)

That leaves moopi's and timzigg's ideas:
I will try Chrome and see what happens (do I download it while I'm using Ubuntu and then just run it, or do I use Wine to run it?)
moopi --  what is the command to run firefox from the terminal?
How do I get a "User Agent Switcher" extension? What does it do?

---

### Post by goog64 on 2010-12-05
> **MooPi said:**
> Start your browser from terminal and check for errors when you log onto your stock trading site. Which version of java and which browser ? If your using Firefox the "User Agent Switcher" extension may help as well

OK, I figured out how to run Firefox from Terminal, but how do I check for errors when logging into my trading site?
(I tried logging in, got the Java error message. Nothing showed up in Terminal.)

---

### Post by cgroza on 2010-12-05
> **goog64 said:**
> OK, I figured out how to run Firefox from Terminal, but how do I check for errors when logging into my trading site?
(I tried logging in, got the Java error message. Nothing showed up in Terminal.)
So it means that java is working OK on your system. I think it is a website thing here.

---

### Post by wangsuda on 2010-12-05
> **cgroza said:**
> So it means that java is working OK on your system. I think it is a website thing here.There are many websites that can run only on IE. My work's website runs only on IE. I have yet to find a way around it, short of using Windows virtually. Sorry I can't be of more help.

---

### Post by TBABill on 2010-12-05
The OP stated Sun Java is installed, but it is useless without the sun java plugin for stated purposes. Is that also installed? Search "java plugin" in synaptic to see.

---

### Post by goog64 on 2010-12-05
> **TBABill said:**
> The OP stated Sun Java is installed, but it is useless without the sun java plugin for stated purposes. Is that also installed? Search "java plugin" in synaptic to see.

Thanks TBABill. I just did as you said. Java plugin is installed.

I tried Chrome for Linux. Didn't work.
moopi, I found that "switcher" you were talking about. Cool program. I mucked around with it for a while. No luck.

---

### Post by goog64 on 2010-12-05
> **wangsuda said:**
> There are many websites that can run only on IE. My work's website runs only on IE. I have yet to find a way around it, short of using Windows virtually. Sorry I can't be of more help.

Wangsuda I think you have been VERY helpful. I think this is the problem.
How do you use Windows virtually?

---

### Post by beew on 2010-12-06
I have not read all the posts so I am not sure if this has been covered. Even if you have installed the latest java Ubuntu would still use OpenJdk as default unless you explicitly set the default to sun-java. To do that just type in the terminal
```

sudo update-java-alternatives -s java-6-sun
```

---

### Post by goog64 on 2010-12-06
> **beew said:**
> I have not read all the posts so I am not sure if this has been covered. Even if you have installed the latest java Ubuntu would still use OpenJdk as default unless you explicitly set the default to sun-java. To do that just type in the terminal
```

sudo update-java-alternatives -s java-6-sun
```

Thanks. I have removed OpenJDK, but I will try it anyway.

---

### Post by goog64 on 2010-12-06
I tried it. I got a whole bunch of lines like this:
update-alternatives: error: no alternatives for xjc.
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/appletviewer

---

### Post by beew on 2010-12-06
That means you haven't have all java 6 components installed. You need, in addition to jre and plugin, also bin and jdk, there may another thing or two but I can't remember off the top of my head. Go check if you have at least these 4 installed from Synaptic, if not, install them and try again.

---

### Post by gradinaruvasile on 2010-12-06
The OP stated that javatester.org confirmed that he had the latest java installed. So probably he has.

I encountered somewhat similar problems on Windows - there was a bank site that used java - worked in Internet Explorer and Chrome, but not in Firefox. There seems to be 2 java plugins involved - the standard java plugin and another one , some J2ee loader (this only exists on Windows AFAIK).

---

### Post by IkeLewis on 2010-12-06
So the best bet may be for the OP to get a version of Internet Explorer working on Wine?

---

### Post by beew on 2010-12-06
Or forget about the website. I refuse to  deal with IE only sites(and fortunately can afford to). Screw them. :) Anyone in these days still pretends IE is the only web browser shouldn't be in the business. An IE only site is an advertisement of cluelessness and technical incompetence as far as I am concerned.

---

### Post by wojox on 2010-12-06
In a terminal what does this tell us:

```
java -version
```

---

### Post by jtarin on 2010-12-06
I have seen no mention of confirmation that the Sun Jav&#1092; plugin is indeed loaded by Firefox. eg:"about: plugins" entered in the url bar.

---

### Post by t0p on 2010-12-06
> **goog64 said:**
> 
How do you use Windows virtually?

This means install [VirtualBox]("http://www.virtualbox.org/"), then use your Windows install disk to install a virtual instance of Windows inside VirtualBox. 

Look [here]("https://help.ubuntu.com/community/Virtualisation") to find out more about virtualization.

---

### Post by blazemore on 2010-12-06
The website is checking for if you are running IE, and then just failing when your browser says you aren't.

What's wrong with a little white lie?

Installing this Firefox addon ([https://addons.mozilla.org/en-US/firefox/addon/59/](https://addons.mozilla.org/en-US/firefox/addon/59/))

use it to change your "user agent string" when you're on that site, and trick it into thinking you're running IE8 on Windows (or some other combination you know to work)

---

### Post by beew on 2010-12-06
> **blazemore said:**
> The website is checking for if you are running IE, and then just failing when your browser says you aren't.

What's wrong with a little white lie?

Installing this Firefox addon ([https://addons.mozilla.org/en-US/firefox/addon/59/](https://addons.mozilla.org/en-US/firefox/addon/59/))

use it to change your "user agent string" when you're on that site, and trick it into thinking you're running IE8 on Windows (or some other combination you know to work)

Have you actually used this addon yourself? If I am not mistaken it only works for FireFox running in Windows.

---

### Post by philinux on 2010-12-06
> **beew said:**
> Have you actually used this addon yourself? If I am not mistaken it only works for FireFox running in Windows.

User agent works just fine on linux running Firefox.

---

### Post by beew on 2010-12-06
> **philinux said:**
> User agent works just fine on linux running Firefox.

It is good to know, thanks.

@OP

Why not post a link to the website and see if we can access it?

---

### Post by walt.smith1960 on 2010-12-06
> **goog64 said:**
> I love Ubuntu 10.04, and I want to be free from Windows, but I cannot log in to my stock trading site with Ubuntu. I get an error message
**Java needs to be installed/upgraded**

I have the latest Java installed. Javatester.org confirms that it is working and I have visited many websites that require Java and they all work fine except this one stock trading site.
Their help desk only supports Windows, so you guys/gals are my only hope. Any ideas?

That's probably because this site only wants to use the most modern and secure software--Windows & I.E. :lolflag:

---

### Post by BlueboxPhone on 2010-12-06
Have you tried Google Chrome? it seems to work for everything I do.

---

### Post by goog64 on 2010-12-06
Wow, thanks for your replies everyone. I will try to answer all your questions:
beew: the site is [https://web.iress.com.au/secure/form.asp](https://web.iress.com.au/secure/form.asp) but the problems only begin when I try to log in (and I don't want to post my login details)

blazemore: I have tried changing the user agent string, but I still got the Java message problem

When I am in Windows, I can access the site using Firefox, I.E. and Chrome.
When I am in Linux, I cannot access the site using Firefox, Chrome nor with Wine running Firefox.
(Wine won't open I.E for me, so I haven't tried that.)
The site's help desk says **Windows is required**

It seems to me that the site knows when I am not using Windows, and for some reason says I have a Java problem. Would using Virtualbox be a way around this? Do you think there's another way to trick the site into thinking I am using Windows?

wojox:     java - version returns this:
[B]java version "1.6.0_22"
Java(TM) SE Runtime Environment (build 1.6.0_22-b04)
Java HotSpot(TM) Client VM (build 17.1-b03, mixed mode, sharing)[/B]

jtarin:    about:plugins returns this:
**Java(TM) Plug-in 1.6.0_22**

 File:  libnpjp2.soVersion:   The next generation [Java]("http://java.sun.com/") plug-in for Mozilla browsers.   MIME Type Description Suffixes Enabled    application/x-java-vm Java&#8482; Plug-in 
Yes   application/x-java-applet Java&#8482; Plug-in Applet 
Yes   application/x-java-applet;version=1.1 Java&#8482; Plug-in 
Yes   application/x-java-applet;version=1.1.1 Java&#8482; Plug-in 
Yes   application/x-java-applet;version=1.1.2 Java&#8482; Plug-in 
Yes   application/x-java-applet;version=1.1.3 Java&#8482; Plug-in 
Yes   application/x-java-applet;version=1.2 Java&#8482; Plug-in 
Yes   application/x-java-applet;version=1.2.1 Java&#8482; Plug-in 
Yes   application/x-java-applet;version=1.2.2 Java&#8482; Plug-in 
Yes   application/x-java-applet;version=1.3 Java&#8482; Plug-in 
Yes   application/x-java-applet;version=1.3.1 Java&#8482; Plug-in 
Yes   application/x-java-applet;version=1.4 Java&#8482; Plug-in 
Yes   application/x-java-applet;version=1.4.1 Java&#8482; Plug-in 
Yes   application/x-java-applet;version=1.4.2 Java&#8482; Plug-in 
Yes   application/x-java-applet;version=1.5 Java&#8482; Plug-in 
Yes   application/x-java-applet;version=1.6 Java&#8482; Plug-in 
Yes   application/x-java-applet;jpi-version=1.6.0_22 Java&#8482; Plug-in 
Yes   application/x-java-bean Java&#8482; Plug-in JavaBeans 
Yes   application/x-java-bean;version=1.1 Java&#8482; Plug-in 
Yes   application/x-java-bean;version=1.1.1 Java&#8482; Plug-in 
Yes   application/x-java-bean;version=1.1.2 Java&#8482; Plug-in 
Yes   application/x-java-bean;version=1.1.3 Java&#8482; Plug-in 
Yes   application/x-java-bean;version=1.2 Java&#8482; Plug-in 
Yes   application/x-java-bean;version=1.2.1 Java&#8482; Plug-in 
Yes   application/x-java-bean;version=1.2.2 Java&#8482; Plug-in 
Yes   application/x-java-bean;version=1.3 Java&#8482; Plug-in 
Yes   application/x-java-bean;version=1.3.1 Java&#8482; Plug-in 
Yes   application/x-java-bean;version=1.4 Java&#8482; Plug-in 
Yes   application/x-java-bean;version=1.4.1 Java&#8482; Plug-in 
Yes   application/x-java-bean;version=1.4.2 Java&#8482; Plug-in 
Yes   application/x-java-bean;version=1.5 Java&#8482; Plug-in 
Yes   application/x-java-bean;version=1.6 Java&#8482; Plug-in 
Yes   application/x-java-bean;jpi-version=1.6.0_22 Java&#8482; Plug-in 
Yes

---

### Post by sp-1070 on 2010-12-06
oke so there is another way not quite easy but do-able you just install Virtualbox ose in wich you install windows with that you can do evry little windows thingy that might come up later but you wont actually be on windows

---

### Post by sydbat on 2010-12-06
> **goog64 said:**
> Wow, thanks for your replies everyone. I will try to answer all your questions:
beew: the site is [https://web.iress.com.au/secure/form.**asp**](https://web.iress.com.au/secure/form.**asp**)That's the problem right there. The site is running a Windows server and has not been configured to accept anything but connections from Windows boxes. Sorry. Nothing ***you*** do, short of dual booting or running Windows virtually will help. ***They*** have to change things on their end.
> The site's help desk says **Windows is required**This confirms what I am saying.

Personally, I would move my investments elsewhere. Do some research to find an institution that has properly configured servers that are OS neutral.

---

### Post by cf0531 on 2010-12-06
Just download virtual box, set up a virtual pc with windows installed on it and do that. Simple solution. If you havent worked with virtual pcs before it's prettyy easy vbox runs you through a wizard and everything.

---

### Post by pricetech on 2010-12-06
Virtualbox is probably your best solution, at least short term.

You can install the OSE version via Synaptic or the PUEL version from the website.  Either will work, but the PUEL version supports USB, and maybe a few other things.

Install the Guest Additions whichever version of VBox you use, and don't try to install any drivers.  VBox will give your OS all the "drivers" it needs.

Long Term Solution:  Find another place to trade.  I wouldn't trust any site that can't use non proprietary web server software with my money.

---

### Post by geoff07 on 2010-12-06
I can recommend virtualbox. I run real xp inside VB3.2.10 under Ubuntu 10.04 for an app that won't behave under Wine and it is very easy to set up and use. You can share USB, printers etc quite easily. You do need the Guest additions to share files but that also is easy.

But really you should close your account and make sure that the management know the reason.

---

### Post by pricetech on 2010-12-06
Forgot to mention, though it probably wouldn't help since the site is looking for a windows box, but Opera is another good browser.  I have used Opera on sites where nothing else works with great success.

---

### Post by DaithiF on 2010-12-06
@OP: A website only knows what O/S you are running from what you tell it in the http request you send ... this goes back to the User-Agent switcher plugin suggestion from earlier in the thread.  I think you said you tried it (setting the user agent to Internet Explorer) and it didn't work, but that in itself may not be enough if the website is testing what platform you are running on, rather than what browser you are running.

My suggestion, install User agent switcher on both your windows and your linux machines.  On windows firefox, go to tools -> default user agent -> user agent switcher -> test... it will bring you to a webpage which tells you exactly what info. you are passing as your user agent, copy the xml and import it into your linux firefox (there is an import button within the Edit User Agents... dialog.  Activate this user agent, and now at least you can be sure that you are pretending reliably to be a windows box running firefox.

Its also possible that the website is running some java code to determine the platform you are on, and throws an error at the java level when it finds its not windows ... if thats the case then you're out of luck, but if its just a http-level check then the user agent approach above should work.

good luck

---

### Post by goog64 on 2010-12-06
Great stuff guys, thanks!!
 
DaithiF, I will try what you said when I get home (I might have to read it a few times to understand it, but it sounds promising.)
 
sydbat, cf0531, pricetech and geoff07, if DaithiF's method doesn't work, it looks like I'll try Virtualbox and thanks for all your advice. 
Pricetech, I really appreciate the detail you put into that explanation, thanks.
 
p.s. I would love to close my trading account and switch to someone who supports Ubuntu, but I'm pretty sure there are none in Australia.

---

### Post by asmoore82 on 2010-12-06
If Firefox on Windows works, Firefox for Windows on WINE has to work.

You may have to downgrade to Firefox 3.0/3.5.
Firefox 3.6 and above have begun actively blacklisting obsolete java versions -
Anything below 1.6u20 or so. A lot of dusty database code out there requires
J-initiator compatibility which goes back to Java 1.3!

Remember for the WINE solution, you have to download Firefox/Java/Flash/Shockwave
*for windows* and install them in the same Wine container.
Firefox in WINE cannot use the real linux flash or java plugins.

The key difference that makes Wine the best solution in theory is that it
does not require a valid windows license; Full-on virtualization does.
The practical advantages of VirtualBox are snapshots and it's just plain awesome.

I've often thought about "packaging" up my wine container with
firefox and all plugins installed and distributing it to help.
But the Wine config/registry isn't portable - it contains my username and
folder structure all over the place. Perhaps I need to make a script to help install.
This script would also avoid all Flash/Shockwave redistribution license issues...

---

### Post by goog64 on 2010-12-06
OK, I tried "pretending" to be Windows/Firefox by using User Agent Switcher, but I still got the same Java error message when trying to log in to the site [https://web.iress.com.au/secure/form.asp](https://web.iress.com.au/secure/form.asp)

That leaves only one more option (I think?) before going with Virtualbox.
I have sent asmoore82 a PM to help me understand how to do the Wine thing he suggests.
Let you know how it goes.

---

### Post by onaridge on 2010-12-06
Chromium which is in the repository works great right out of the box. :-)

---

### Post by NCLI on 2010-12-06
> **onaridge said:**
> Chromium which is in the repository works great right out of the box. :-)
Please read the thread before posting ;)
> **goog64 said:**
> OK, I tried "pretending" to be Windows/Firefox by using User Agent Switcher, but I still got the same Java error message when trying to log in to the site [https://web.iress.com.au/secure/form.asp](https://web.iress.com.au/secure/form.asp)

That leaves only one more option (I think?) before going with Virtualbox.
I have sent asmoore82 a PM to help me understand how to do the Wine thing he suggests.
Let you know how it goes.
What asmoore82 means is that you have to install the windows versions of firefox, java and flash through wine, then try.

---

### Post by goog64 on 2010-12-06
Thanks NCLI, I tried it, but no luck.
Somehow, that $%#@ website still knows I'm not using Windows.
I even tried changing User Agent Switcher in my functioning Windows Firefox to make the website think I was Ubuntu, but it let me log in anyway!! It knew I was really using Windows!

---

### Post by zipteye on 2010-12-06
Do you mid posting the website address?

---

### Post by BryanMtdt on 2010-12-06
Have you tried logging here?

[http://www.iress.com.au/information/info_w_login.asp](http://www.iress.com.au/information/info_w_login.asp)

I don't use it so I can't find much more.

---

### Post by goog64 on 2010-12-06
Thanks Bryan. I gave it a shot - same result.
I'm about to download Virtualbox.

---

### Post by asmoore82 on 2010-12-07
Proudly presenting the DrunkFox Script - the easy way to get Firefox on Wine.

For unknown reasons,
1. Firefox 3.6 under Wine freezes on loading flash player - using Firefox 3.5 instead.
2. the newest flash installer is really crashy - persistence pays off.

---

### Post by jwbrase on 2010-12-07
As was mentioned earlier, the problem is that the server is serving *.asp files, which need certain Windows-only(?) software to decode. So even if you tell it you're using IE on Windows, it will still know you don't have the proper software. You may be able to get it working with certain Mono packages, but I'm not sure, that's just a thought I had when looking through the Wikipedia article on [ASP.NET]("http://en.wikipedia.org/wiki/ASP.NET"). 

Failing that, you're pretty much stuck with finding another site. 

As far as finding another site, just because they say "we don't support Linux" doesn't mean it won't work with Linux. It just means that if it turns out not to work with Linux, they won't try and fix it so it does, and they won't hold your hand to help you get it to work if you call their Tech Support about it.

But most of the time, unless they're using a closed standard like *.asp, Linux will handle it just fine, even though they're not *trying* to allow Linux to handle it. Still, unless they specifically say they support Linux, you can't know until you open an account with them whether it will work with Linux, unless you can find another Linux user that trades stocks that can recommend the site.

---

### Post by asmoore82 on 2010-12-07
> **jwbrase said:**
> As was mentioned earlier, the problem is that the server is serving *.asp files, which need certain Windows-only(?) software to decode. So even if you tell it you're using IE on Windows, it will still know you don't have the proper software. You may be able to get it working with certain Mono packages, but I'm not sure, that's just a thought I had when looking through the Wikipedia article on [ASP.NET]("http://en.wikipedia.org/wiki/ASP.NET").

You've gotten it a little mixed up.

ASP, PHP, Ruby on Rails, mod-python, etc. are all server-side code. The server, *not* your browser, runs the code and sends the result to your browser to be rendered. All the browser sees is the resulting HTML, XHTML, CSS and Javascript. Like ubuntuforums.org, for example, you do *not* need any PHP installed on your machine to use this site.

For the sites that really don't work, it's because they are sending broken HTML, etc. to be rendered on IE, the broken browser. This is not an inherent problem with ASP.NET, it's just web developers who don't know or don't care - either way, it would be fair to call them at least mentally lazy, partially incompetent, and possibly even vindictive.

But even this is not the case here, because it is known to work with Firefox on Windows. It may require some obscure browser plugin, like J-initiator, which wouldn't be a deal breaker, or Microsoft's DRM, which likely would be a deal breaker. But there is no way a website can immediately distinguish between Firefox on Windows and Firefox in Wine.

---

### Post by goog64 on 2010-12-07
Thanks JW and AS. I did run Firefox in Wine, but still couldn't log in. I tried Firefox 3.1.5 and 3.5. (I have a VERY bad internet connection, so I want bonus points for diligence here!)
I like your idea of finding someone who already trades stocks using Linux.
Time for a new thread about that, in case Virtualbox is too slow when I try it for the first time later tonight.

---

### Post by goog64 on 2010-12-07
I cannot log in to web.iress.com.au to trade stocks. They are Windows only. (I've spent 5 days trying to get around it, but no luck.) So I would like to know if there are any trading options out there for Linux?

My trades are $33 each up to $200,000, so if your brokerage is much more than that, I'll have to stick with Windoze!

---

### Post by robbie d on 2010-12-07
can you use wine to install a version of IE????

---

### Post by kaldor on 2010-12-07
> **goog64 said:**
> I cannot log in to web.iress.com.au to trade stocks. They are Windows only. (I've spent 5 days trying to get around it, but no luck.) So I would like to know if there are any trading options out there for Linux?

My trades are $33 each up to $200,000, so if your brokerage is much more than that, I'll have to stick with Windoze!

Try using the user agent switcher addon for Firefox. It might help, because it can disguise your browser as IE.

Edit: Do not even bother with WINE and IE.

---

### Post by uRock on 2010-12-07
Merged triplicate threads. Please do not create multiple threads on the same issue.

Thanks,
uRock

---

### Post by goog64 on 2010-12-07
> **uRock said:**
> Merged triplicate threads. Please do not create multiple threads on the same issue.

Thanks,
uRock

Sorry, I thought that finding a Linux-friendly stock trading site would count as a different topic from learning how to access a "Linux-unfriendly" site.
But I note that the responses are indeed the same as has been discussed already in the "how-to-access" thread.

(The third related thread was just my bad memory - sorry.)

---

### Post by asmoore82 on 2010-12-07
Have you tried the DrunkFox Script?
[http://ubuntuforums.org/showpost.php?p=10209854&postcount=51](http://ubuntuforums.org/showpost.php?p=10209854&postcount=51)

Does the site ask for any additional plugins?

---

### Post by zipteye on 2010-12-07
> **blazemore said:**
> The website is checking for if you are running IE, and then just failing when your browser says you aren't.
 
What's wrong with a little white lie?
 
Installing this Firefox addon ([https://addons.mozilla.org/en-US/firefox/addon/59/](https://addons.mozilla.org/en-US/firefox/addon/59/))
 
use it to change your "user agent string" when you're on that site, and trick it into thinking you're running IE8 on Windows (or some other combination you know to work)
 
Nope.
The 'requirements' for his website say I.E. or Firefox.
However, it also says winows operating system. (I'll get to that)
 
The .asp issue would only be relevant if the .asp pages used VBScript, but if Firefox is supported, that has to mean that they are using Javascript. VBScript does not function in FireFox.
 
It has to be a Java issue with his Ubuntu install.
(Well, it doesnt have to be, but... you know)
 
He should contact the web admin and ask what's going on.
Why is there the requirement of a Windows operating system?
If it was a .HTA app, I could understand it.
If it was VBScript .asp, I could understand it.
 
Otherwise...
Ubuntu Java and, or, Firefox Java is not right.
Or, they lie on their system requirements.
Or, the site is broken.

---

### Post by zipteye on 2010-12-08
> **zipteye said:**
> Nope.
The 'requirements' for his website say I.E. or Firefox.
However, it also says winows operating system. (I'll get to that)
 
The .asp issue would only be relevant if the .asp pages used VBScript, but if Firefox is supported, that has to mean that they are using Javascript. VBScript does not function in FireFox.
 
It has to be a Java issue with his Ubuntu install.
(Well, it doesnt have to be, but... you know)
 
He should contact the web admin and ask what's going on.
Why is there the requirement of a Windows operating system?
If it was a .HTA app, I could understand it.
If it was VBScript .asp, I could understand it.
 
Otherwise...
Ubuntu Java and, or, Firefox Java is not right.
Or, they lie on their system requirements.
Or, the site is broken.

They can tell what the O.S. is by using navigator.platform, but why they would check for that is beyond me.

---

### Post by goog64 on 2010-12-08
> **zipteye said:**
> Nope.
The 'requirements' for his website say I.E. or Firefox.
However, it also says winows operating system. (I'll get to that)
 
The .asp issue would only be relevant if the .asp pages used VBScript, but if Firefox is supported, that has to mean that they are using Javascript. VBScript does not function in FireFox.
 
It has to be a Java issue with his Ubuntu install.
(Well, it doesnt have to be, but... you know)
 
He should contact the web admin and ask what's going on.
Why is there the requirement of a Windows operating system?
If it was a .HTA app, I could understand it.
If it was VBScript .asp, I could understand it.
 
Otherwise...
Ubuntu Java and, or, Firefox Java is not right.
Or, they lie on their system requirements.
Or, the site is broken.

Thanks zipteye; I only partly understand what you are saying, bur you have given me renewed hope!
I have been waiting two days to hear from the site's help desk.
asmoore82, I will try the drunkfox later today when I get home, thanks.

---

### Post by zipteye on 2010-12-08
While running FireFox under Wine, Instead of [http://,](http://,) type this in the web browsers address bar:
 
javascript:navigator.platform
 
Then hit return.
What does it display for operating system?

---

### Post by goog64 on 2010-12-08
> **zipteye said:**
> While running FireFox under Wine, Instead of [http://,](http://,) type this in the web browsers address bar:
 
javascript:navigator.platform
 
Then hit return.
What does it display for operating system?

Thanks zipteye. I did that and got:  Win32

---

### Post by goog64 on 2010-12-08
> **asmoore82 said:**
> Proudly presenting the DrunkFox Script - the easy way to get Firefox on Wine.

For unknown reasons,
1. Firefox 3.6 under Wine freezes on loading flash player - using Firefox 3.5 instead.
2. the newest flash installer is really crashy - persistence pays off.

asmoore82, I downloaded DrunkFox, but I didn't know what to do with it??
I extracted it, then double-clicked on it, but that just opened it in gedit?
How do I use it? What does it do?
Thanks for your help.

---

### Post by zipteye on 2010-12-08
Ok, if you did that with FireFox running in Wine, then the website thinks you're running windows.
That takes care of their 'Windows Operating System' requirement.
 
Now, I'm just going to go through a few things here that might seem dumb, but I think we have to cover as many possibilites as we can.
 
Launch FireFox under Wine, click on the FireFox tools menu, select Options, then click on the Content option.
Make sure 'Enable JavaScript' is check-marked.
Click on the Andvanced Option. Click on the Encryption Tab. Check mark both Use SSL and Use TLS.
 
When you are done with that, go back to the Tools menu and choose Add-ons.
Click on Extensions. Click on 'Find Updates'. Let it install any java extensions it may find.
After that, click on 'Plugins'. Look to see if there are Java Plugins in the list.
If there are some, you can try clicking 'Find Updates'.
If not, click on 'Get Add-ons' and type Java in the search box.

---

### Post by goog64 on 2010-12-09
Than you so much for your help zipteye; I really appreciate it. (And nothing you suggest could be too dumb!)
Enable Javascript, SSL and TLS are all ticked.

The only thing that appears in 'Extensions' is User Agent Switcher. Nothing else.

If I search Add-ons for Java, all I get are these 3:
Javascript Debugger
Javascript Deobfuscator
Javascript Options

If I Browse All Ad-ons for Java, I get a few "Java Consoles" like 6.0.02,
but if I try to install one, then when I restart Firefox, it says that this console is useless (can't remember the exact words) and will be un-installed next time Firefox starts.

In Plugins, I have two for Java:
Java Deployment Toolkit 6.0.140.8
Java (TM) Platform SE 6 U14

There is no "Find Updates" button in Plugins.

By the way, earlier today I sent an email to the web.iress.au website help desk. I politely asked your questions from a few posts back. I just got a reply which basically said "as I told you in my last email, we don't support Ubuntu." 
So you are my only hope!!

---

### Post by zipteye on 2010-12-09
<snip>

---

### Post by zipteye on 2010-12-09
Pfffft...

Well, the User Agent Switcher certainly works to disguise the browser while running straight from Ubuntu.

Going back to your original error message...

If you look here:
[HTML]
http://www.java.com/en/download/linux_manual.jsp?locale=en&host=www.java.com[/HTML]It has a Linux (self-extracting file) with an instructions link, but it's kind of hairy.
Don't know if it is something you want to tackle or not.
It didn't look too appealing to me.

Perhaps someone more advanced than me can make a script for you that will handle the whole installation.

That Sun Java installation, combined with 'User agent Switcher' pointed to Internet Explorer 8, will probably do the trick running straight from Ubuntu.

But...
I'm out of steam and have reached the end of my puny abilities to help you.

It probably is because of openJDK vs. Sun Java as others have pointed out.

---

### Post by Paddy Landau on 2010-12-09
> **zipteye said:**
> They can tell what the O.S. is by using navigator.platform, but why they would check for that is beyond me.
It may be worth asking the help desk, "Why?" The only reason I can think of for such a restriction is that it's easier to install malware on Windows, but I'm sure they have their reasons.

I suppose that they prevent Mac users too?

Check the contract that you signed. If it doesn't explicitly state Windows is required, you can ask for a refund or for them to buy you a Windows operating system.

---

### Post by goog64 on 2010-12-09
> **zipteye said:**
> Pfffft...

If you look here:
[HTML]
http://www.java.com/en/download/linux_manual.jsp?locale=en&host=www.java.com[/HTML]It has a Linux (self-extracting file) with an instructions link, but it's kind of hairy.
Don't know if it is something you want to tackle or not.
It didn't look too appealing to me.

Perhaps someone more advanced than me can make a script for you that will handle the whole installation.

That Sun Java installation, combined with 'User agent Switcher' pointed to Internet Explorer 8, will probably do the trick running straight from Ubuntu.



Thanks zipteye, I'll try it. Nothing to lose except more time I guess.

---

### Post by goog64 on 2010-12-09
> **Paddy Landau said:**
> It may be worth asking the help desk, "Why?" The only 
I suppose that they prevent Mac users too?

Check the contract that you signed. If it doesn't explicitly state Windows is required, you can ask for a refund or for them to buy you a Windows operating system.

Yes, they do prevent Mac also.
But there's no contract, and it didn't cost me to join - I just want to be able to log in from Ubuntu.

---

### Post by fluxlizard on 2010-12-09
Try installing user agent switcher in firefox and once installed under tools menu in firefox go to default user agent and select internet explorer 8 under the menu. Do this when you are actually at the site before you log in.

---

### Post by goog64 on 2010-12-09
> **fluxlizard said:**
> Try installing user agent switcher in firefox and once installed under tools menu in firefox go to default user agent and select internet explorer 8 under the menu. Do this when you are actually at the site before you log in.

Tried it with IE 6, 7 and 8. No luck. still get the Java error message.

There has been a new development in the case:
I tried to log in again (using Firefox in Wine with standard default user agent) and I got a DIFFERENT error message:

[COLOR=DarkRed]A script on this page may be busy, or it may have stopped responding. You can stop the script now, or you can continue to see if the script will complete.

Script: [https://web.iress.com.au/base.asp?ts=20101210125426&install=:27](https://web.iress.com.au/base.asp?ts=20101210125426&install=:27)[/COLOR]

Whether I click on "continue" or "stop", the page goes to "logging on please wait". Unfortunately, I have been waiting ten minutes and nothing else happens.
Any ideas?

---

### Post by Paddy Landau on 2010-12-10
The site's system requirements say, inter alia:
> Apple Macintosh is not supported to run this product. Apple Macintosh   browsers do not support the *Java installation technology used by Internet   Explorer* on Windows.(Emphasis mine.) This makes me think that it uses an Internet Explorer-specific program on your machine, and possibly a Windows-specific Java program. If I'm right, it won't work without Windows. A virtual machine or dual boot would be your only options, provided your machine is powerful enough to handle Windows.

---

### Post by zipteye on 2010-12-10
Here ya go:
 
[URL="http://support.mozilla.com/en-US/kb/warning%20Unresponsive%20script"][HTML] 
http://support.mozilla.com/en-US/kb/warning%20Unresponsive%20script
[/HTML][/URL]
 
Options (fixes) for that error message while using Firefox.

---

### Post by asmoore82 on 2010-12-10
> **goog64 said:**
> asmoore82, I downloaded DrunkFox, but I didn't know what to do with it??
I extracted it, then double-clicked on it, but that just opened it in gedit?
How do I use it? What does it do?
Thanks for your help.

You need to give it executable permission,
Right-click -> "Properties" -> "Permissions" Tab

> Apple Macintosh is not supported to run this product. Apple Macintosh browsers do not support the Java installation technology used by Internet Explorer on Windows.

This is sounding more and more like the Oracle J-Initiator Plug-in.

---

