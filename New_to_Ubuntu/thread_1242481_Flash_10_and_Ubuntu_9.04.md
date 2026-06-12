---
title: "Flash 10 and Ubuntu 9.04"
date: 2009-08-17
forum: New to Ubuntu
---

### Post by KyleRickards on 2009-08-17
Hi all

Another silly question time (sorry) - I seem unable to get Flash 10 running within Ubuntu, despite accepting the plug in suggestions or downloading from Adobe.

Since doing the above, I don't get the missing plug in's message but things like Facebook games and the BBC Iplayer no longer seem to actually run?

Thanks in advance 
Kyle

---

### Post by jrothwell97 on 2009-08-17
Don't worry: it's a common problem :)

The easiest way to get Flash working is to install flashplugin-nonfree using Synaptic. If you want to save time, you can do it using the terminal instead:

```
sudo apt-get install flashplugin-nonfree
```

---

### Post by KyleRickards on 2009-08-17
Thanks jrothwell97, I tried that, seemed to be installing, I closed Firefox and reopened but still nothing, do I need to uninstall anything before I follow your advice? Or is there something I need to enable within Firefox? (On the Iplayer, it looks like it will work on TV and Radio and then just says Content not available)

Thanks for help.

Kyle

Further Edit: When I go to the Adobe site, the demo animation works straight off as do Youtube now so I wonder what the other issue is...

---

### Post by Shig on 2009-08-17
Hi

Are you running a 32bit or 64bit system?

Also, can you please navigate to the following URL in Firefox and post the output for the flash plugin?
```
about:plugins
```

A couple of URLs for pages that do not work for you would also be really helpful.

---

### Post by KyleRickards on 2009-08-17
Hi

32 bit and here is what it says.

BBC Iplayer and any flash based game on Facebook don't seem to work now.

**Shockwave Flash**

 File name:  libswfdecmozilla.so Shockwave Flash 9.0 r999   MIME Type Description Suffixes Enabled    application/x-shockwave-flash Adobe Flash movie swf Yes   application/futuresplash FutureSplash movie spl Yes

---

### Post by Shig on 2009-08-17
You are using the swfdec plugin, which is not the Adobe plugin.
To remove it, run:
```
sudo apt-get remove swfdec-mozilla
```

You will then need to download and then install the latest Adobe version, as the swfdec plugin does not work for everything.

You can grab the latest Adobe .deb installer from [here]("http://get.adobe.com/flashplayer/")
Make sure you choose ".deb for Ubuntu 8.04+" from the drop-down menu to get the correct package. Once downloaded you should be able to simply double-click to install.

After restarting firefox, the plugins page should show libflashplayer.so instead of libswfdecmozilla.so

---

### Post by KyleRickards on 2009-08-17
Thanks Shig! All working, am very very grateful!

Kyle

---

### Post by acornbrain on 2009-09-19
Yes, this worked for me as well! Thank goodness, I was about to give up. Removing swfdec-mozilla seemed to be the key. Flash works fine now. Those of you experiencing choppy flash videos may also be helped by this advice.

Yay, another win for Ubuntu

---

### Post by NoaHall on 2009-09-19
Or if you want to download the videos from iPlayer, check out the link in my sig. Note - don't use it against the terms and conditions of iPlayer ( no keeping the files longer than 30 days, no using it to transfer to someone outside the uk)

---

### Post by piperdown10 on 2009-09-19
I'm still having trouble with this. I've installed the Adobe Flash 10 .deb and removed swfdec-mozilla and I'm still getting very choppy flash video playback with little or no audio. I'm on a 32bit system. Also, I'm not really sure where to type the "about:plugins" command.

---

### Post by KyleRickards on 2009-09-19
Hi piperdown10 - you type it in the address bar of Firefox **about: plugins** (no space  when you put it in).

Hope this helps.

Kyle

---

### Post by piperdown10 on 2009-09-19
> **KyleRickards said:**
> Hi piperdown10 - you type it in the address bar of Firefox **about: plugins** (no space  when you put it in).

Hope this helps.

Kyle

It did! Thanks Kyle!

Here's the output:

    File name: libgnashplugin.so
    Shockwave Flash 9.0 r999. Gnash 0.8.5, the GNU SWF Player

Also:

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes

---

### Post by KyleRickards on 2009-09-19
I can't believe I am understanding some of this, about a month ago I was clueless!

The plug-in you have there is a third party one still. I would remove it using the console and then make sure that you have the Adobe one in your plug-ins. Mine says the following (after the guys here massively helped me) 

File name:  libflashplayer.so 
Shockwave Flash 10.0 r32
application/x-shockwave-flash Shockwave Flash swf Yes   
application/futuresplash FutureSplash Player spl Yes

---

### Post by NoaHall on 2009-09-19
gnash sucks. Get the proper nonfree flash.

---

### Post by piperdown10 on 2009-09-19
So I tried removing with:

```
sudo apt-get remove libgnashplugin.so
```

and no dice. I tried it without the extension too. It's not in Synaptic either.

---

### Post by NoaHall on 2009-09-19
sudo apt-get remove gnash

---

### Post by KyleRickards on 2009-09-19
Are you using Firefox or Flock?

---

### Post by piperdown10 on 2009-09-19
> **NoaHall said:**
> sudo apt-get remove gnash

Done. Thank you.

> **KyleRickards said:**
> Are you using Firefox or Flock?

Firefox 3.0.14

---

### Post by NoaHall on 2009-09-19
now do ```
 sudo apt-get install flashplugin-nonfree 
```

---

### Post by piperdown10 on 2009-09-19
It said it was already the newest version. So I just went and tried it. It works great! :KS

Thank you so much Kyle and Noa. I really appreciate the help! :)

---

### Post by Sixjokers on 2009-09-19
ok try not to laugh to much lol  I just got Ubuntu because Vista 64 decided to tell me that i put too much new hardware in my computer and they will not validate my $300 copy of it any more so i decided to try Ubuntu 64. So far i am liking it, like i said only been hours though. I cannot get the flashplayer to work i tried doing everything that was said on this as of downloading the nonfree one and try to erase the other one but said i did not have it so no need to delete it. so i am pretty stuck any help would be awsome



lol nevermind i figured it out thanx thou

---

### Post by Onael on 2009-10-17
Hi guys,

I'm new to Linux and so far I am very impressed. However, I can't seem to fix my flashplugin issue. I've tried to remove and change the plugin but I can't seem to get it right.

This is the output:

File name:  libswfdecmozilla.so
                Shockwave Flash 9.0 r999


I've already downloaded the .deb from adobe, but I can't get these plugins to uninstall. Is there a command to uninstall all flashplugins so that I can do fresh installs of the correct plugins?

Thank you



update: I went through and re-read this threat and found all the answers to my questions. Everything is working fine now.

File name:  libflashplayer.so
Shockwave Flash 10.0 r32

MIME                                        Type                                    Description                                 Suffixes                Enabled
application/x-shockwave-flash           Shockwave Flash                         swf                             Yes   
application/futuresplash                             FutureSplash Player                 spl                              Yes

 Thank you guys for your clear and very helpful posts. Playing facebook games was the only reason I had to boot to windows. Now let's see how long I can stay on Ubuntu lol

---

