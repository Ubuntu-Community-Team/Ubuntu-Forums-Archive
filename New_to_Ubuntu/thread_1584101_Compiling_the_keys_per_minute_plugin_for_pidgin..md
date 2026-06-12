---
title: "Compiling the keys per minute plugin for pidgin."
date: 2010-09-28
forum: New to Ubuntu
---

### Post by klikevil on 2010-09-28
Okay so I want to compile a plugin i found here [http://3d.benjamin-thaut.de/?p=12](http://3d.benjamin-thaut.de/?p=12)

But the README is no help whatsoever

> 
keysperminute plugin for the pidgin messager ([www.pidgin.im]("http://www.pidgin.im")) 
It counts the key strokes per minute while you are typing a message and generates a small statistic about it. 
 
See COPYRIGHT for the copyright 
See COPYING for the licence 
 
INSTALL 
======= 
On windows copy the alienfx-notification.dll to YOUR-USER-DIR/App Data/.purple/plugins/ 
 
On linux you need to compile it yourself. 
 
After successfully installing it you need to activate it in the pidgin plugins manager 
 
COMPILE 
======= 
follow the official compiling guidelines for plugins on [www.pidgin.im]("http://www.pidgin.im")


I'm currently using Pidgin 2.6.6 (libpurple 2.6.6).   When I attempt to compile the plugin it bitches about glib headers missing

```

seotechd ~/SearchCheck/man/keysperminute $ gcc -o keysperminute.so keysperminute.c
keysperminute.c:24:18: error: glib.h: No such file or directory
keysperminute.c:27:22: error: internal.h: No such file or directory
keysperminute.c:28:20: error: pidgin.h: No such file or directory
keysperminute.c:30:19: error: debug.h: No such file or directory
keysperminute.c:31:20: error: notify.h: No such file or directory
keysperminute.c:32:21: error: signals.h: No such file or directory
keysperminute.c:33:18: error: util.h: No such file or directory
keysperminute.c:34:21: error: version.h: No such file or directory
keysperminute.c:36:23: error: gtkplugin.h: No such file or directory
keysperminute.c:37:22: error: gtkprefs.h: No such file or directory
keysperminute.c:38:22: error: gtkutils.h: No such file or directory
keysperminute.c:39:24: error: gtkconvwin.h: No such file or directory
keysperminute.c:42: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;LastKeyStroke&#8217;
keysperminute.c:43: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;LastMessage&#8217;
keysperminute.c:54: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
keysperminute.c: In function &#8216;ComputeTimeDiff&#8217;:
keysperminute.c:57: error: &#8216;GTimeVal&#8217; undeclared (first use in this function)
keysperminute.c:57: error: (Each undeclared identifier is reported only once
keysperminute.c:57: error: for each function it appears in.)
keysperminute.c:57: error: expected &#8216;;&#8217; before &#8216;tCurrentTime&#8217;
keysperminute.c:58: error: &#8216;tCurrentTime&#8217; undeclared (first use in this function)
keysperminute.c:59: error: &#8216;LastKeyStroke&#8217; undeclared (first use in this function)
keysperminute.c:59: error: &#8216;G_USEC_PER_SEC&#8217; undeclared (first use in this function)
keysperminute.c: In function &#8216;ComputeMessageDiff&#8217;:
keysperminute.c:64: error: &#8216;GTimeVal&#8217; undeclared (first use in this function)
keysperminute.c:64: error: expected &#8216;;&#8217; before &#8216;tCurrentTime&#8217;
keysperminute.c:65: error: &#8216;tCurrentTime&#8217; undeclared (first use in this function)
keysperminute.c:66: error: &#8216;LastMessage&#8217; undeclared (first use in this function)
keysperminute.c:66: error: &#8216;G_USEC_PER_SEC&#8217; undeclared (first use in this function)
keysperminute.c: In function &#8216;ResetTime&#8217;:
keysperminute.c:71: error: &#8216;LastKeyStroke&#8217; undeclared (first use in this function)
keysperminute.c: In function &#8216;ResetMessageTime&#8217;:
keysperminute.c:75: error: &#8216;LastMessage&#8217; undeclared (first use in this function)
keysperminute.c: At top level:
keysperminute.c:78: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
keysperminute.c:93: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
keysperminute.c:136: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
keysperminute.c: In function &#8216;show_stats&#8217;:
keysperminute.c:172: error: &#8216;gchar&#8217; undeclared (first use in this function)
keysperminute.c:172: error: expected &#8216;;&#8217; before &#8216;Output&#8217;
keysperminute.c:176: error: &#8216;Output&#8217; undeclared (first use in this function)
keysperminute.c:177: error: &#8216;keysperminute_plugin_handle&#8217; undeclared (first use in this function)
keysperminute.c:177: error: &#8216;PURPLE_NOTIFY_MSG_INFO&#8217; undeclared (first use in this function)
keysperminute.c: At top level:
keysperminute.c:180: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
keysperminute.c: In function &#8216;SaveStats&#8217;:
keysperminute.c:194: error: &#8216;gchar&#8217; undeclared (first use in this function)
keysperminute.c:194: error: &#8216;Filename&#8217; undeclared (first use in this function)
keysperminute.c: In function &#8216;LoadStats&#8217;:
keysperminute.c:214: error: &#8216;gchar&#8217; undeclared (first use in this function)
keysperminute.c:214: error: &#8216;Filename&#8217; undeclared (first use in this function)
keysperminute.c: At top level:
keysperminute.c:233: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
keysperminute.c:256: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
keysperminute.c:274: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;plugin_load&#8217;
keysperminute.c:299: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;plugin_unload&#8217;
keysperminute.c:319: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;info&#8217;
keysperminute.c:352: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
keysperminute.c: In function &#8216;PURPLE_INIT_PLUGIN&#8217;:
keysperminute.c:356: error: expected &#8216;{&#8217; at end of input
seotechd ~/SearchCheck/man/keysperminute $ 

```Any suggestions?

---

### Post by andrewthomas on 2010-09-29
First, make sure you have the packages necessary to build.

```
sudo apt-get install build-essential
```If you run into problems, you can consult these two links.

[https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)

[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

---

### Post by klikevil on 2010-09-29
I definitely have build-essential, but thanks for the reply, i will look in to those inks.

[EDIT] unfortunately, neither of those links is of any use to me in this situation, this source code in particular does not come with a ./configure just a single .c file that is going to have to be GCC'd somehow.

---

### Post by andrewthomas on 2010-09-29
no configure.ac file?

---

### Post by klikevil on 2010-09-29
> **andrewthomas said:**
> no configure.ac file?

This is all it came with, and no instructions on HOW to compile it for linux just a single file source code, and a compiled dll for windows users.  By looking at the source it looks like it should be able to compile on linux with no issues since they don't use anything that is exclusive to windows in it, I just can't figure out how.

---

### Post by andrewthomas on 2010-09-29
You have done
```
  sudo apt-get build-dep pidgin
```

correct?

---

### Post by klikevil on 2010-09-29
Yes, maybe I shouldn't have posted this in ABSOLUTE beginner talk lol.

---

