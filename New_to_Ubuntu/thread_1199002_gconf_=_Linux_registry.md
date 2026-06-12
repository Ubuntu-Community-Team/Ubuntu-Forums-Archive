---
title: "gconf = Linux registry?"
date: 2009-06-28
forum: New to Ubuntu
---

### Post by Andy06 on 2009-06-28
Gconf is pretty much the Linux version of the windows registry right?

I mean it has settings for all sorts of apps, components and modules which can all be modifying from one place overruling the settings made through the GUI in the respective apps. Hell its even organised like the windows registry with the global settings and per user ones.

My question is, why doesn't it have security? Have I set it up wrong?
I mean seriously, linux password authentication is far more annoying than UAC, it asks me before it even lets me change the system date and time and do mundane things but anyone can walk into the gconf editor without a password and do whatever they like?

Is that a massive security hole or have I set up my authorisations wrong??

Thanks

---

### Post by binbash on 2009-06-28
One is user based other (system date and time) is system based.There is no security hole or system weakness here.

---

### Post by philinux on 2009-06-28
gconf is only your users settings. No one elses.

---

### Post by niteshifter on 2009-06-28
Hi,

No, it is not like the Win registry, just bears a passing resemblance to it. There's nothing in there that deals with the nitty-gritty of networking, for example. Or the kernel. Or system security. All of which (plus much more) are in Win's registry.

It's not a security hole: Those are *your* settings it displays. Another user's view of GNOME's configuration can be totally different.

---

### Post by Andy06 on 2009-06-28
Thanks for explaining that.

---

### Post by Martje_001 on 2009-06-28
Gconf is gnome's registry. You wouldn't find it on a KDE system like Kubuntu.

The G in Gconf actually stands for Gnome.

---

### Post by &#1082;&#1086;&#1084;&#1084;&#1091;&#1085;&#1080;&#1089;&#1090;&#1080;&#1095;&#1077;&#1089;&#1082; on 2009-06-28
Difference is Gconf does not tie into the system. Gconf only handles Gnome applications. Gconf is actually a useful program.

---

### Post by CatKiller on 2009-06-28
> **Andy06 said:**
> Gconf is pretty much the Linux version of the windows registry right?

I mean it has settings for all sorts of apps, components and modules which can all be modifying from one place overruling the settings made through the GUI in the respective apps. Hell its even organised like the windows registry with the global settings and per user ones.

No. The Gnome Configuration system is almost nothing like the Windows Registry. The only thing they have in common is a passing resemblance in the way that the information is displayed, and that is simply because that's an intuitive way to lay out hierarchical information. If you look, you'll see that your file manager does exactly the same thing.

GConf-Editor does not "overrule" any settings anywhere; they are the same setting! Pick any application that has a configuration key in GConf that can be expressed through the Preferences screen for that application. Change the setting in the Preferences, and see how it changes in GConf-Editor. Now change the setting in GConf-Editor, and see the setting change in the Preferences window.

The Windows Registry is a binary file; it is a program that must be run to put a particular layout in memory. It is vulnerable to a buffer overflow attack from a particularly configured registry key. It contains sytem settings, application settings, user settings, hardware settings, all kinds of rubbish, all mixed together, so to have permission to change a user setting you also need permission to change hardware and system settings. Because the file contains so much stuff it becomes huge, and because it has to be loaded into memory to work, fragmentation is a big problem for system performance.

The Gnome Configuration system is a hierarchy of XML files. You can edit them with any text editor you choose. It only contains application settings. Applications already know which line of which file contains the setting that they need, because they put them there, so they don't need to scan through a huge memory array to find the setting that they need. They just read a line from a text file, the same as most configuration under a GNU/Linux system.

They aren't constructed the same and they don't act the same. They are nothing alike.

The reason you need permission to change the time and not to use the GConf-Editor is because changing the system time affects all users, whereas anything that you do with GConf-Editor only changes the configuration of applications for your user.

---

### Post by egalvan on 2009-06-28
CatKiller, thanks for that post,
excellent explanations.

EGalvan

---

### Post by Andy06 on 2009-06-29
Yep thanks for that!

Very comprehensive.

---

