---
title: "Can't Find Java under Synaptics"
date: 2009-05-12
forum: New to Ubuntu
---

### Post by banduan on 2009-05-12
I installed Sun Java under add/remove programs. I use Intrepid 64.

Unfortunately, checking the version with java -version shows that despite me having used add/remove to remove open JDK and Iced Tea, they're still there.

java.com also verifies my newly installed Java as being outdated!

More distressing, I can't do a bit of problem-solving by first removing the java I'd just installed using add/remove programs.

It asks me to use synaptics. Synaptics does not list Java. What repository do I find Java under?

Btw: I can't find Icedtea or OpenJDK under synaptics either.

---

### Post by kpkeerthi on 2009-05-12
After installing Sun JDK, you need to select it as the default java for your system:

1. Open a Terminal window
2. Run ```
sudo update-alternatives --config java
```
3. Follow the onscreen prompt 

You also need to install sun-java6-plugin if you need firefox plugin.
```
sudo apt-get install sun-java6-plugin
```

[http://www.ubuntugeek.com/how-to-install-java-runtime-environment-jre-in-ubuntu-904-jaunty.html]("http://www.ubuntugeek.com/how-to-install-java-runtime-environment-jre-in-ubuntu-904-jaunty.html")

---

### Post by banduan on 2009-05-13
Thanks for how to set defaults that worked well. 

However apt can't find the plugin.
Add/Remove programs says the plugin is unsupported!

I'm also uncomfortable with the fact that I can't find Java under synaptics (keep in mind I'm under Intrepid). I was sure there was a repository for that though, under Intrepid?

---

### Post by kpkeerthi on 2009-05-13
[http://packages.ubuntu.com/intrepid/sun-java6-plugin]("http://packages.ubuntu.com/intrepid/sun-java6-plugin")

---

### Post by gandaran on 2009-05-13
theres no sun-java plugin for 64-bits in intrepid but you can use the icedtea plugin, (type icedtea in search box, it's there in synaptic) or go to the java.com website and download the 64-bits java package.
or upgrade to jaunty 9.04.

---

### Post by banduan on 2009-05-13
> **gandaran said:**
> theres no sun-java plugin for 64-bits in intrepid.

Ugh. Me upgrading to Jaunty is not an option until the sound issues are sorted out.

Mayhaps I have to use java.com's binary install. Dislike it very much because the old files are left lying around.

---

### Post by gandaran on 2009-05-13
> **banduan said:**
> Ugh. Me upgrading to Jaunty is not an option until the sound issues are sorted out.

Mayhaps I have to use java.com's binary install. Dislike it very much because the old files are left lying around.
I have an idea, grab the sun-java6 packages (plugin, bin, jre, and java common) from jaunty 9.04 repository, they should work with intrepid too
here you can download the 64-bits plugin [http://packages.ubuntu.com/jaunty/sun-java6-plugin](http://packages.ubuntu.com/jaunty/sun-java6-plugin) but you need to remove the 32-bits java if installed and install the 64-bits jre and bin files.

---

