---
title: "Firefox closes because of Java?"
date: 2009-08-11
forum: New to Ubuntu
---

### Post by ramoj02 on 2009-08-11
Hello.

Every time I go to a page that uses Java, like runescape.com, javatester.org, or games.yahoo.com, my Firefox just closes with no message or anything. How do I fix this?

Thanks in advance.

---

### Post by arky on 2009-08-12
Maybe firefox is crashing out on you. Can you provide the distro and OS version. 

Also enabled apport to generate a crash report

$ force_start=1 /etc/init.d/apport start
$ firefox

---

### Post by TheForumTroll on 2009-08-12
Happens here too even though it used to work so I'll listen in ;)

I get this error:

```

Didn't find JVM under /usr/lib/firefox-addons/plugins

```
and this:
```

 ../../../../src/plugin/solaris/plugin2/common/JavaVM.c:104: InitializeJVM: Assertion `foundJVM' failed.

```

---

### Post by mthalis on 2009-08-12
Did you install Java? this Error is missing Java virtual machine

---

### Post by ramoj02 on 2009-08-12
> **arky said:**
> Maybe firefox is crashing out on you. Can you provide the distro and OS version. 

Also enabled apport to generate a crash report

$ force_start=1 /etc/init.d/apport start
$ firefox

I'm using UNR 9.04 (Jaunty) on Acer Aspire One.

And I enabled apport to generate a crash report, then I went to a site that uses Java and my Firefox closed and gave me a meassge. It says:

"Sorry the program "firefox" closed unexpectedly.

---

### Post by TheForumTroll on 2009-08-12
Is Java installed? Look in "about:plugins" in Firefox.

I fixed the error I just had like this:
```

sudo rm -r /usr/lib/firefox-addons/plugins/libnpjp2.so
sudo ln -s /usr/lib/jvm/jre1.6.0_13/lib/amd64/libnpjp2.so /usr/lib/firefox-addons/plugins/

```

Looks like Java was updated so the link broke.

---

### Post by mthalis on 2009-08-12
After searching net I got this
[https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/278581](https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/278581)

---

### Post by ramoj02 on 2009-08-12
> **TheForumTroll said:**
> Is Java installed? Look in "about:plugins" in Firefox.

I fixed the error I just had like this:
```

sudo rm -r /usr/lib/firefox-addons/plugins/libnpjp2.so
sudo ln -s /usr/lib/jvm/jre1.6.0_13/lib/amd64/libnpjp2.so /usr/lib/firefox-addons/plugins/

```

Looks like Java was updated so the link broke.

Yes. I'm pretty sure Java is installed.

And when I run:

sudo rm -r /usr/lib/firefox-addons/plugins/libnpjp.so

I get:

rm: cannot remove `/usr/lib/firefox-addons/plugins/libnpjp2.so': No such file or directory

---

### Post by TheForumTroll on 2009-08-12
The lines wasn't supposed to be copy&pasted ;)

You have to create the symlink in the correct folder.

Type about:config in Firefox and look for a lot of Java stuff. If it is not there the Java plugin is not installed.

---

### Post by ramoj02 on 2009-08-12
> **TheForumTroll said:**
> The lines wasn't supposed to be copy&pasted ;)

You have to create the symlink in the correct folder.

Type about:config in Firefox and look for a lot of Java stuff. If it is not there the Java plugin is not installed.

Everything is installed properly and I created the symlink in the right folder.

I went to javatester.org to test if everything worked, it showed me my Java version and Firefox just suddenly closes after 2 seconds or so.

---

### Post by TheForumTroll on 2009-08-12
Try this:
Open a shell, run firefox (just type firefox and hit enter). When it crashes look at the last line(s) it printed in the shell.

---

### Post by ramoj02 on 2009-08-14
Finally, I FIXED IT!

What I did was, first, I installed the OFFICIAL Sun Java. After that, I removed OpenJDK through Synaptics. That's it.

---

### Post by green0eggs on 2009-08-15
Just to say I had the same problem: Firefox closing unexpectedly when using Java apps. 

Which I solved by removing the OpenJDK package (I already had the official Sun package installed) as above.

Thanks ramoj02

---

### Post by Eric Warren on 2009-09-18
[U][I][B]Step 1)  un-install java.

Step 2) re-install

if that does not work try this.

step 3) edit the jre-jdk but does it crash and make a icon on you're desktop?
if it does then i know the problem it says something like hserror3748ydg38 or something that's easy to fix if it says that email me at [email]activeric@hotmail.com[/email] il get back too you a.s.a.p
[/B][/I][/U]

---

