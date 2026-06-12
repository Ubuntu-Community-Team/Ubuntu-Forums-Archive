---
title: "Slimming down Ubuntu"
date: 2010-07-04
forum: New to Ubuntu
---

### Post by Speed Racer on 2010-07-04
Is it possible to slim Ubuntu down? I 've noticed there is a lot of things I don't use that come preinstalled (IE bluetooth) and I was wondering if I could remove these things or at least stop them from starting upon boot?

Sorry if this is the wrong place to post this

---

### Post by Dennis N on 2010-07-04
If you don't need it, bluetooth can be safely disabled by unchecking it in 'Services' which is found under the System menu in the top panel.

---

### Post by A_M_S on 2010-07-04
You can remove the applications you dont need. Ubuntu is very modular an configurable.
There are also try xubuntu if you have old hardware.
[http://www.xubuntu.org/](http://www.xubuntu.org/)

---

### Post by JC Cheloven on 2010-07-04
You could:
- Uninstalling apps & disabling startup services from regular Ubuntu, as suggested.
- Trying out a lighter version. I'd suggest [LUbuntu]("http://lubuntu.net/").
- Do some [minimal instalation]("https://help.ubuntu.com/community/Installation#Minimal%20installations") and install only what you want/need afterwards. Requires more knowlegde though.

If you haven't performance problems, and you're not really inclined to master the "guts" of your system, my advice would be to stick with the default setup. Makes life easier ;-)

---

### Post by ajgreeny on 2010-07-04
The only way that I know to easily stop bluetooth running is to install and use bum (boot up manager).  Services is no longer available in the menu for 10.04.

You can also use synaptic to search (name only) for bluetooth, then carefully see what happens when you ask to uninstall them one by one.  Several of them can be removed without taking something else that you need, but there are at least two lib files that attempt to take out half your system files, so leave those alone.

I have removed several applications like that, but as I say, you must be very careful and look to see what else is going to go with it.

---

### Post by Paqman on 2010-07-04
> **JC Cheloven said:**
> 
- Do some [minimal instalation]("https://help.ubuntu.com/community/Installation#Minimal%20installations") and install only what you want/need afterwards. Requires more knowlegde though.


The script in my sig makes it pretty straightforward.

---

### Post by Speed Racer on 2010-07-04
I think after I learn about ubuntu more I will try that minimal install. A friend turned me on to linux after I had major issues with windows thanks for the input

---

### Post by sandyd on 2010-07-04
> **Speed Racer said:**
> I think after I learn about ubuntu more I will try that minimal install. A friend turned me on to linux after I had major issues with windows thanks for the input
if you want really minimal, you can try a distribution of Linux called [Gentoo]("http://gentoo.org")

---

### Post by -kg- on 2010-07-04
> **ajgreeny said:**
> The only way that I know to easily stop bluetooth running is to install and use bum (boot up manager).  Services is no longer available in the menu for 10.04.

**System/Preferences/Startup Applications**

You can stop whichever things are started at log in that you don't need to have running.  The Bluetooth application is among those on the list.  I have quite a long list, which I think I might go through.

---

### Post by k3lt01 on 2010-07-05
> **Speed Racer said:**
> Is it possible to slim Ubuntu down? I 've noticed there is a lot of things I don't use that come preinstalled (IE bluetooth) and I was wondering if I could remove these things or at least stop them from starting upon boot?

Sorry if this is the wrong place to post thisGetting back to the OP, there are a couple of things you can do that will help put Ubuntu on a diet, not that it really needs it but I do know what you mean.

1st, I would advise you to follow the [first post in this thread]("http://ubuntuforums.org/showthread.php?t=140920").

2nd, Now you have number 1 setup you can go through Synaptic and carefully select what programs you don't want. Someone already mentioned, using Bluetooth as the example, that you can do a search and select for removal anything bluetooth related that is installed.

One word of warning, make sure you select one thing at a time and make sure you check what other applications are also removed if you remove the one you just selected. I always remove Bluetooth and Evolution but you cannot remove ALL of these two applications as some of them are required by Ubuntu for it to function properly. So be a wise consumer and make sure you read the "fine print" before you do actually remove something.

Now you have done number two, go back to number one and check your Orphan and your autoremove packages and you will find you can do this a number of times till it stops showing Orphaned programs. Doing this will slim down Ubuntu alot.

My laptop is a near standard install but my desktop doesn't have anything like Empathy or OpenOffice on it as it is basically my entertainment unit so it only has a bar minimum of things I need.

Hope this helps.

---

### Post by Jakiejake on 2010-07-05
> **Speed Racer said:**
> Is it possible to slim Ubuntu down? I 've noticed there is a lot of things I don't use that come preinstalled (IE bluetooth) and I was wondering if I could remove these things or at least stop them from starting upon boot?

Sorry if this is the wrong place to post this

Or you can go Tiny Core Or DSL (Damn Small Linux) they've got around a 4-6 second or so boot time

---

### Post by k3lt01 on 2010-07-05
Here is [another link]("https://help.ubuntu.com/community/Diet%20Ubuntu")

---

### Post by ajgreeny on 2010-07-05
> **-kg- said:**
> **System/Preferences/Startup Applications**

You can stop whichever things are started at log in that you don't need to have running.  The Bluetooth application is among those on the list.  I have quite a long list, which I think I might go through.
That's just the bluetooth manager applet, not bluetooth itself, I think.

Install bum to stop services running the easy way, or uninstall if you want to, but as I say, be careful.

---

### Post by yetiman64 on 2010-07-05
> **ajgreeny said:**
> That's just the bluetooth manager applet, not bluetooth itself, **I think.**

Install bum to stop services running the easy way, or uninstall if you want to, but as I say, be careful.

**Correct**, I just turned it off here (as per -kg-'s post) and only lost the system tray applet, looked in system monitor and noted the main Bluetooth process still running. _B.U.M. is required_ to stop Bluetooth.

---

### Post by k3lt01 on 2010-07-05
> **yetiman64 said:**
> **Correct**, I just turned it off here (as per -kg-'s post) and only lost the system tray applet, looked in system monitor and noted the main Bluetooth process still running. _B.U.M. is required_ to stop Bluetooth.**Incorrect** B.U.M. is not required to stop Bluetooth, you don't need to install anything to stop something, all you need to do is uninstall the Non-Essential parts. That will stop Bluetooth.

The OP wants to slim his system down, not install more into it.

---

### Post by yetiman64 on 2010-07-05
> **k3lt01 said:**
> **Incorrect** B.U.M. is not required to stop Bluetooth, you don't need to install anything to stop something, all you need to do is uninstall the Non-Essential parts. That will stop Bluetooth.

The OP wants to slim his system down, not install more into it.

My comment **correct** was referring to what ajgreeny **thought** only, ie that the **System/Preferences/Startup Applications** suggestion by -kg- will only stop the applet and not the main Bluetooth process.

I have read the whole post and realize that ultimately the OP wants to slim down the system but please revisit the OPs first post and note the comment,
> ....or at least stop them from starting upon boot?
To stop bluetooth at startup would require what ajgreeny said, as I tested -kg-'s suggestion and noted it doesn't stop bluetooth - hence my post. Check it out yourself.;)

Whether the OP goes with shutting a service down (by adding a package) or ripping out parts of the system will depend on how experienced / game the OP is (we are after all in the absolute beginner talk section :)).

---

### Post by -kg- on 2010-07-05
> **yetiman64 said:**
> **Correct**, I just turned it off here (as per -kg-'s post) and only lost the system tray applet, looked in system monitor and noted the main Bluetooth process still running. _B.U.M. is required_ to stop Bluetooth.

Interesting.  I turned it off, logged out and logged back in, and I can't find anything to do with Bluetooth running in System Monitor.  What is the name of the "main Bluetooth process"?

---

### Post by yetiman64 on 2010-07-05
> **-kg- said:**
> Interesting.  I turned it off, logged out and logged back in, and I can't find anything to do with Bluetooth running in System Monitor.  What is the name of the "main Bluetooth process"?
Are you showing All processes in the view menu?

Edit: with all processes showing in system monitor the process still running is the one marked as a worker thread. Note I still have the applet running at the moment. The applet is what the startup entry will remove only.

---

### Post by stmiller on 2010-07-05
Evolution also has a lot of crap running in the background by default in Ubuntu. Turn that off too.

I'd say go with Debian if you want slim. Otherwise yeah you'll have to turn off all of those unneeded services in Ubuntu.

I wish Ubuntu had a service manager like Centos/Redhat:

[http://www.centos.org/docs/5/html/Deployment_Guide-en-US/s1-services-serviceconf.html](http://www.centos.org/docs/5/html/Deployment_Guide-en-US/s1-services-serviceconf.html)

---

### Post by mike555 on 2010-07-05
if you don't use "Ubuntu one" you could turn it off....

---

### Post by NightwishFan on 2010-07-05
Did you check out: Boot Up Manager?
[http://www.marzocca.net/linux/bum.html](http://www.marzocca.net/linux/bum.html)

To install: [Boot Up Manager]("apt://bum")

---

### Post by k3lt01 on 2010-07-05
> **yetiman64 said:**
> My comment **correct** was referring to what ajgreeny **thought** only, ie that the **System/Preferences/Startup Applications** suggestion by -kg- will only stop the applet and not the main Bluetooth process.

I have read the whole post and realize that ultimately the OP wants to slim down the system but please revisit the OPs first post and note the comment,
To stop bluetooth at startup would require what ajgreeny said, as I tested -kg-'s suggestion and noted it doesn't stop bluetooth - hence my post. Check it out yourself.;)

Whether the OP goes with shutting a service down (by adding a package) or ripping out parts of the system will depend on how experienced / game the OP is (we are after all in the absolute beginner talk section :)).I have checked out for myself your post and what you were commenting on and I stand by my comment based on this comment of yours
> **yetiman64 said:**
> **Correct**, I just turned it off here (as per -kg-'s post) and only lost the system tray applet, looked in system monitor and noted the main Bluetooth process still running.**_B.U.M. is required_ to stop Bluetooth.**The underlining is yours the bolding is mine to emphasise your underlining.

As I said I stand by my comment B.U.M. is not required to stop Bluetooth. It is an option but not a necessity. Couple this with the OPs apparent desire to slim his system down (if he can) installing another application (in my mind at least) will just add more bloat when the OP is wanting less.

---

### Post by yetiman64 on 2010-07-06
@k3lt01,
I'll _concede that it's probably not necessary in all or even most cases_ to use B.U.M. now, after working through the issues via PM with -kg- today. 

On some hardware to completely shutdown bluetooth (read my laptop on which I tested - Acer with built in bluetooth module and killswitch) it is necessary for me apparently, and may be the case for others as well. Hardware specific it's appearing with regards to bluetooth modules.

Just keep in mind to balance out the inherent risks in stripping packages from Ubuntu and the valid cautions ajgreeny expressed in earlier posts versus an 85.2 KB download of and 532 KB disk space requirements for B.U.M. (figures taken from Synaptic). Its memory resources etc are only utilized as its being used to configure the system, AFAICT. 

These figures don't appear as "bloat" imo, but as a useful tool for the OP to manage services etc.

yetiman64.

@OP, sorry for any distractions caused, if you feel it's so. Hope my input is of some use to you.  Good luck, yetiman64.

---

### Post by k3lt01 on 2010-07-06
yeti, no need to concede anything. I was commenting on a small portion of your post because you emphasised it making it appear as it was a must have application. That is all my comment was about.

As for the Acer issue. Acer must have changed a bit, my laptop is an Acer, my fathers laptop is an Acer and I have disabled Bluetooth on both without resorting to adding anything. You may want to consider investigating that further and filing a bug report.

btw, I define bloat as anything not required regardless of size, if it isn't needed and its on there it is just taking up space.

---

### Post by yetiman64 on 2010-07-06
OK mate. My mistake on the emphasis, no extra application is must have -true, but it turned out to be an interesting day of hardware checking behind the scenes (btw Acer is Travelmate8200 series if it means anything to you). Cheers and see you around :).

---

