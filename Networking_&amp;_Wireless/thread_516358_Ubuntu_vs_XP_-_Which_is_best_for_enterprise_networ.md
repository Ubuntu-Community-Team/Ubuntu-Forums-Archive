---
title: "Ubuntu vs XP - Which is best for enterprise networking? A:XP"
date: 2007-08-03
forum: Networking &amp; Wireless
---

### Post by muddymind on 2007-08-03
That's right... You may say everything U want about linux, but U can't say it's the best when it comes to enterprise networking...

I've been trying to connect a workstation on my company's network for almost 4 days and I simply can't make it work... You my say that I'm a windows fanboy or a linux noob but that isn't true... I've been using linux for almost 2 years as my main OS in my laptop (which is my only pc) and I've been very happy with it and I've done everything with it... 

On Tuesday my superior told me that I was going to try to make a linux workstation to someday replace some windows workstations but if I don't make it work in the following days I can surely say that it will never happen...

This network works on a windows 2003 server with active directory and Isa proxy and with a fresh install of windows it's working in less than 5 minutes... in linux?

ISA Proxy: You may try to set the proxy address and authentication in System->Preferences->Network Proxy and you'll notice that it doesn't work with anything (firefox, gaim, apt, etc)... Now I must ask... What the hell is that for? To tease you with a tool that doesn't work?
I tried ntlmaps and managed to put everything working (but I had to put proxy configuration on every app I wanted to use which isn't what I want...) but with that I have a big problem... I want each user with it's own authentication on the proxy that would be determined by his logon... I search everyplace in the internet to work it out but I only see people on the net complaining about this deficiency and all of them use ntlmaps or export http_proxy that doesn't do what I want...

active directory: Well... this one is funny... I did a lot of howto's to put it work and none of them worked... what the hell?!?!? this is one of the major features of almost every enterprise network on earth and there aren't any decent tools for it? I managed to put kerberos to get authentication tickets but could manage to put it working with the login...

Is linux really for human beings or for super nerds :-\"

---

### Post by kevinlyfellow on 2007-08-03
I can understand frustration with these things, but instead of posting threads looking for flame wars, I suggest submitting bug reports, so that developers can get an idea of the needs of enterprise users.  Many companies have successfully deployed linux and have greatly benefited from it, but it isn't for every business setup.  So let's keep it at that ok?

---

### Post by muddymind on 2007-08-03
> **kevinlyfellow said:**
> I can understand frustration with these things, but instead of posting threads looking for flame wars, I suggest submitting bug reports, so that developers can get an idea of the needs of enterprise users.  Many companies have successfully deployed linux and have greatly benefited from it, but it isn't for every business setup.  So let's keep it at that ok?

This isn't a flame... it's the thruth... 
Why didn't I submitted a bug report? Because it was already submited 6 months ago and nothing changed... 
The argument of other companies already deployed linux isn't valid... now linux is just for some companies? c'mon let's face it... linux has major flaws when it comes to networking...

[]

ps-if someone can came up with some idea to solve my problems don't be shy and share it :)

---

### Post by lynx75 on 2007-08-03
I'm thinking that WINDOWS is much easier for the human beings than linux. 

A normal user can use laptops or desktops without any problem with windows, instead the linux system is more complicated. 
For example, I'm spend a lot of my free time to try and install my vodafone connect card e620, without any results, I'm asked to help me but at the moment no one replied to me.

Windows desktop & servers is the most suitable system in the world for the human beings, at the moment. 

Linux (every distros) are still complicated for a normal users, and in some cases for an expert user , as well.

I'm work with computers since 1987, and no one can't spent a lot of time only to configure for example a simple pcmcia card in linux, in windows you spent only some minutes, and that's all ...it's working. Our time it is very important...

that's all for me....

---

### Post by yota on 2007-08-03
> **muddymind said:**
> 
active directory: Well... this one is funny... I did a lot of howto's to put it work and none of them worked... what the hell?!?!? this is one of the major features of almost every enterprise network on earth and there aren't any decent tools for it? I managed to put kerberos to get authentication tickets but could manage to put it working with the login...

Is linux really for human beings or for super nerds :-\"

I think this is a case of a [Well intentioned troll]("http://ubuntuforums.org/showthread.php?t=58017") (no offense meant at all)

I understand your frustration IMHO all of you problem are not coming by linux, but by the fact that you are trying to integrate it in a purely windows environment... And is known that microsoft does not help that much when someone wants interoperability.
Do you think that the opposite would be much easier? Think about putting a single windows workstation in a purely unix world; how long would take for you to authenticate against nis or to see a simple nfs share?
Please note that "windows networking" is not "networking".

Apart from the perspective which seems biased to me, I agree that AD is a service of huge success and can be a pain trying to integrate linux with it.

---

### Post by Anteaus on 2007-08-03
> **lynx75 said:**
> I've worked with computers since 1987

I've more than a decade of Windows-support experience, and in that time I've absorbed  a tremendous amount of knowledge, possibly without realising it. That makes fixing Windows problems seem relatively easy. I have to ask myself if the reverse had been true, had I been working on *nix for that length of time, would I find Windows difficult? Probably yes.

As for Active Directory, why make things complicated if they don't need to be? The NT4 style of domain is still  supported by Samba, and is much more functional for small networks.  Anyone who's had dealings with Windows AD servers knows that while they may integrate large LANs better, they also create enormous headaches.

One of the biggest headaches for an AD admin is the way in which many aspects of the AD cannot easily be changed once set, at least not without major upheaval. You only have to look at the number of posts on the MS boards such as, "My company has changed its domain-name, now I just need to change the domain-name in AD to match..." Yeah. Good luck, you'll need it. 

This is one instance in which Linux' use of config-files (not unlike earler Windows .ini files, which MS unwisely abandoned in favour of the Registry) is a superior arrangement. If the config-file has the right commands then the software will work as intended, and a change of config is a simple matter of replacing the file and restarting the process.  

BTW If it's any help there is a freeware utility which will allow a WinXP desktop to log-on graphically to a SMB server without the need for AD membership. 
[http://mylogon.net](http://mylogon.net)
saves an awful lot of hair-tearing-out on small LANs.

---

### Post by muddymind on 2007-08-03
> **yota said:**
> I think this is a case of a [Well intentioned troll]("http://ubuntuforums.org/showthread.php?t=58017") (no offense meant at all)

I understand your frustration IMHO all of you problem are not coming by linux, but by the fact that you are trying to integrate it in a purely windows environment... And is known that microsoft does not help that much when someone wants interoperability.
Do you think that the opposite would be much easier? Think about putting a single windows workstation in a purely unix world; how long would take for you to authenticate against nis or to see a simple nfs share?
Please note that "windows networking" is not "networking".

Apart from the perspective which seems biased to me, I agree that AD is a service of huge success and can be a pain trying to integrate linux with it.

ok... now i'm a troll... a troll that follow tutorials like [these]("https://help.ubuntu.com/community/ActiveDirectoryHowto") and when he finds things like
"set up /etc/pam.d/common-auth, e.g. 

    auth    sufficient      pam_krb5.so ccache=/tmp/krb5cc_%u
    auth    sufficient      pam_unix.so likeauth nullok use_first_pass
    auth    required        pam_deny.so
"

and can't login at all (because of the pam_deny.so) then he really is a troll... But if he tries to do other tutorials like [these]("http://developer.novell.com/wiki/index.php/HOWTO:_Configure_Ubuntu_for_Active_Directory_Authentication") and in the end it makes no authentication at all then he continues to be a troll...
give me a break... I already did the oposite way (install a windows workstation in a linux envionment) and it didn't take me days to do it but less than 3 or 4 hours...

BTW... AD from MS have Kerberos support so I wouldn't say that there isn't compatability...

---

### Post by yota on 2007-08-03
> **muddymind said:**
> ok... now i'm a troll... 

Sorry, I didn't want to be rude, it's just that your post seemed to me more a rant than a real help request. Moreover the thread I linked before explains very well that, despite the best intentions, a "If I can't use it, nobody can" implicit assumption does not lead to the right conclusions. Please take just a minute to read it and see if it can help you to slightly change your approach on how linux should work.

The set-the-proxy-in-every-applications problem, for instance, seems to me the same both on windows and linux: if you set the proxy in IE it does not apply automatically to firefox, avast and winamp just to say some. Both OS have a centralized settings which some applications use and other not.

Beeing more constructive the howto [https://help.ubuntu.com/community/ActiveDirectoryHowto](https://help.ubuntu.com/community/ActiveDirectoryHowto) worked for me, and I'm able to authenticate against a Win 2003 AD.

Since you say that you are able to receive a ticket with kinit, I suppose you have already correctly configured /etc/krb5.conf, so the problem is likely with pam (look at /var/log/auth.log for more info about it)
My /etc/pam.d/common-auth looks like this:
```

auth    sufficient      pam_krb5.so ccache=/tmp/krb5cc_%u
auth    sufficient      pam_unix.so likeauth nullok use_first_pass
auth    required       pam_unix.so nullok_secure

```
Have you installed libpam-krb5 and created a local user with the same username of the one defined in AD?

Hope this helps!

---

