---
title: "Java 6.23"
date: 2011-01-29
forum: New to Ubuntu
---

### Post by Dr Small on 2011-01-29
I am trying to install Java 6.23 which is needed for a game (for a family member) and have followed [this page](http://java.com/en/download/linux_manual.jsp?host=java.com&returnPage=http://www.pogo.com/misc/sun-java/success.jsp&locale=en_US&brand=pogo&footer=free) but Firefox won't seem to see the new plugin.

Here's what I've done:
Downloaded "Linux (self-extracting file)"
Moved it to /usr/java
Given it executable permissions (+x)
Executed it...
Added a symbolic link from /usr/java/jre1.6.0_23/plugin/i386/ns7/libjavaplugin_oji.so to /usr/lib/mozilla/plugins

And when I check in about:config, it doesn't show up.

Can anyone help out? I've been working on this problem for hours.

Thanks!
Dr Small

---

### Post by oldos2er on 2011-01-29
See [http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)
I think you're missing the *sudo update-alternatives...* step.

---

### Post by YesWeCan on 2011-01-29
[http://www.oracle.com/technetwork/java/javase/manual-plugin-install-linux-136395.html](http://www.oracle.com/technetwork/java/javase/manual-plugin-install-linux-136395.html)

This works.

---

### Post by Dr Small on 2011-02-07
> **oldos2er said:**
> See [http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)
I think you're missing the *sudo update-alternatives...* step.
I followed the entire guide, and java is still not working. I removed all the icedtea plugin stuff, so the system acts as if there isn't any java installed at all, yet I followed this guide to the tee and ran the *sudo update-alternates* step...

Any other suggestions? Java is there, but Firefox isn't seeing it.

---

### Post by ratcheer on 2011-02-07
> **Dr Small said:**
> 

Any other suggestions? Java is there, but Firefox isn't seeing it.

```

cd /usr/lib/firefox-addons/plugins
sudo ln -s /usr/java/jre1.6.0_23/lib/i386/libnpjp2.so

```

In the ln-s command, /usr/java may be different on your system, depending on where you installed java.

Tim

---

### Post by Dr Small on 2011-02-08
> **ratcheer said:**
> ```

cd /usr/lib/firefox-addons/plugins
sudo ln -s /usr/java/jre1.6.0_23/lib/i386/libnpjp2.so

```

In the ln-s command, /usr/java may be different on your system, depending on where you installed java.

Tim
That did the trick! Thanks for all the help everyone!

Dr Small

---

### Post by ratcheer on 2011-02-08
> **Dr Small said:**
> That did the trick! Thanks for all the help everyone!

Dr Small

I am glad I could help.

Tim

---

