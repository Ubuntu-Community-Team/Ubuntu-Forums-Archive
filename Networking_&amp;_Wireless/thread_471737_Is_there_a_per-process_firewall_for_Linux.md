---
title: "Is there a per-process firewall for Linux?"
date: 2007-06-12
forum: Networking &amp; Wireless
---

### Post by xp_newbie on 2007-06-12
I know about iptables and its qualities - but it allows/disallows communication on a per-port per protocol (TCP/UDP/ICMP) basis. Once I open port 80, for example, ANY process can use it to undesireably "sneak out" information to who-knows-where.

When I say "ANY process" I am not referring to open source stuff but rather to all those commercial applications that are offered now for free - in exchange for agreeing to let it spy on you...

In the Windows world there are numerous products (categorized as "Personal Firewalls") that let the user know when a process is trying to send something to the Internet and let him/her decide whether to allow it or not. Hence the "per-application" or "per-process" name.

Is there anything like that for Linux?

I heard of something like SElinux, but I am not sure what it is. Is it an attempt to provide similar functionality to what I described above?

Thanks,
Alex

---

### Post by az on 2007-06-12
Is there anything like that for linux?  No, there is not.

An applications firewall is just as insecure as the underlying OS.  You don't need any firewall on a free-libre open source desktop system, be it a packet-filter firewall or an applications firewall.  That's why no one has written one.

---

### Post by xp_newbie on 2007-06-12
> **az said:**
> An applications firewall is just as insecure as the underlying OS.  You don't need any firewall on a free-libre open source desktop system, be it a packet-filter firewall or an applications firewall.  That's why no one has written one.

It seems that I didn't ask my question in the clearest form: I don't need a per-process firewall to protect against so called "free-libre open source" programs. I need it to protect against **non-open** source programs (usually commercial). Perhaps your system is 100% open source (good for you), but many Ubuntu users install additional **non-open** source software like Adobe (formerly Macromedia) Flash, Acrobat Reader, Skype, etc.

They all come with a sugar-coated disclaimer which they call "privacy policy" (when in fact it should be named "non-privacy policy"). But you never know when they are going to [abuse your trust]("http://www.wired.com/politics/security/commentary/securitymatters/2005/11/69601") and use it to spy on you (or even to install a backdoor). Certainly limiting yourself to open-source software only is better than any per-application firewall, but we are living in the real world and some of us install (on Linux) non-open-source software.

Thus, I stand my question: Is there a per-process firewall for Linux?

Thanks,
Alex

---

### Post by az on 2007-06-12
> **xp_newbie said:**
>  Perhaps your system is 100% open source (good for you), but many Ubuntu users install additional **non-open** source software like Adobe (formerly Macromedia) Flash, Acrobat Reader, Skype, etc.

They all come with a sugar-coated disclaimer which they call "privacy policy" (when in fact it should be named "non-privacy policy"). But you never know when they are going to [abuse your trust]("http://www.wired.com/politics/security/commentary/securitymatters/2005/11/69601") and use it to spy on you (or even to install a backdoor). Certainly limiting yourself to open-source software only is better than any per-application firewall, but we are living in the real world and some of us install (on Linux) non-open-source software.

Thus, I stand my question: Is there a per-process firewall for Linux?

Thanks,
Alex

No,there is not.  DesktopSecure was in the Dapper-commercial repos, but it doesn't work as it is supposed to.

What you can do, howerver, is more reliably see what these apps are doing than in windows.  Either using command-line tools, or a graphical frontend to the kernel firewall, you can even look at individual packets if you like.

---

### Post by t4thfavor on 2007-06-12
wouldnt wireshark, or tcpdump be able to tell you where and what is leaving your network? I know what your asking, but I am also fairly sure there is no implementation for linux. Guess you could try to stay as close as possible to free/open source as possible, or when your not using stuff lock the network down completely. I have dialup, so I know when there is something sneaking out my pipe. It's happening when the lights are blinking, and im not doing anything.

---

### Post by xp_newbie on 2007-06-12
> **az said:**
> No,there is not.  DesktopSecure was in the Dapper-commercial repos, but it doesn't work as it is supposed to.

Thanks, az. As you probably understand by now, my philosophy is that even if there is a per-process firewall for Linux, it's no good **if it is non-open** source (commercial?).

The reason is simple: In this crazy world, the same tool that is supposed to protect you from spyware, can itself be spyware... Don't believe me? Read here:

[Is your firewall spying on you?]("http://www.theinquirer.net/default.aspx?article=29157")

"Just Because You’re Paranoid Doesn’t Mean They Aren’t Out to Get You". :lol::lol::lol:

Alex

---

### Post by xp_newbie on 2007-06-12
> **t4thfavor said:**
> wouldnt wireshark, or tcpdump be able to tell you where and what is leaving your network? 

Absolutely. But I was looking (for a friend - a layman PC user that wants to use Ubuntu instead of Windows) for something more automatic and easy to use. Similar to ZoneAlarm, Sygate Personal Firewall, etc. on Windows.

Thanks,
Alex

---

### Post by yagood on 2007-06-29
Sorry for the bump, but maybe TuxGuardian will fit your needs:

[http://tuxguardian.sourceforge.net/](http://tuxguardian.sourceforge.net/)

---

