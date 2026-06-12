---
title: "Pidgin Plugins"
date: 2009-05-19
forum: New to Ubuntu
---

### Post by sideffects on 2009-05-19
I downloaded a Pidgin plug in (tar.gz) and extracted it. All of it's files are in a folder and I've been looking where to move that folder for 30 minutes. Any help at is is greatly appreciated.

---

### Post by HDave on 2009-05-19
~/.purple/plugins

(don't ask me where the "purple" comes from)

---

### Post by sideffects on 2009-05-19
Disregard that last statement :)

Thanks for the help. Got it!

---

### Post by asmoore82 on 2009-05-19
> **HDave said:**
> ~/.purple/plugins

(don't ask me where the "purple" comes from)

in Gaim, the internal name for the library that implements the AIM protocol was something like libprpl
the devteam came to pronounce it "lib purple" colloquially.

So when the name Gaim had to be dropped and Pidgin was born,
they embraced the nickname whole-heartedly and just renamed it libpurple entirely:
```
~$ dpkg-query -l libpurple0
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  libpurple0     1:2.5.5-1ubunt multi-protocol instant messaging library
```

I guess pidgin data is stored there as a reminder that libpurple is more than just pidgin,
it is the pidgin project's open source gift to the world, a shared library available to all -
sort of the same way firefox's data is stored in .mozilla

I more or less made this last bit up but it sounds good, right?

---

### Post by sideffects on 2009-05-20
> **HDave said:**
> ~/.purple/plugins

(don't ask me where the "purple" comes from)

I copied the plugin to that folder and the plugin wouldn't show up, so I restarted Pidging. It still didn't show up in my plugins list. Any ideas?

---

### Post by HDave on 2009-05-20
Is the ".so" file in the plug-ins directory...it should be there all by itself (not in a subdirectory, etc.).  

If it is, then perhaps it is version incompatible?  Check your logs.  Trying logging all the way out and then back in.

When I did it (I am using the AWN plugin) all I did was drop the "so" file in that directory and it came up in the list when I restarted.

---

### Post by sideffects on 2009-05-20
> **HDave said:**
> Is the ".so" file in the plug-ins directory...it should be there all by itself (not in a subdirectory, etc.).  

If it is, then perhaps it is version incompatible?  Check your logs.  Trying logging all the way out and then back in.

When I did it (I am using the AWN plugin) all I did was drop the "so" file in that directory and it came up in the list when I restarted.

Okay, I added "plugins" folder, so does it need to be named "plug-ins" like you said?

---

### Post by Mornedhel on 2009-05-20
> **asmoore82 said:**
> I guess pidgin data is stored there as a reminder that libpurple is more than just pidgin, it is the pidgin project's open source gift to the world, a shared library available to all -
sort of the same way firefox's data is stored in .mozilla

I more or less made this last bit up but it sounds good, right?

Actually, I would guess it's because Finch (the console version of Pidgin) also uses libpurple and shares this folder. Any client using libpurple presumably does so to connect to IM services, and thus there is no reason it should not have access to this folder (which also happens to contain conversation logs, avatars and other stuff).

Disclaimer : I also more or less made this up.

---

### Post by HDave on 2009-05-20
> **sideffects said:**
> so does it need to be named "plug-ins" like you said?

That's right..."~/.purple/plugins".

If the "plugins" folder isn't there...make it and drop in your addin's ".so" file.

---

