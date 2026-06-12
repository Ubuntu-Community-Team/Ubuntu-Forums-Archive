---
title: "Installing tar"
date: 2010-06-01
forum: New to Ubuntu
---

### Post by jrab227 on 2010-06-01
I'm really not understanding how to install programs, especially since on my jolicloud distro, ./configure doesn't work. I attempted to install Eclipse on here and I ended up using the tar command and extracting. But now nothing actually works. I tried to use sudo apt-get install eclipse, but that just tells me the program's already installed. I did install it before and I removed it, but now the apt-get thinks its still installed. Also, how does the file system work? When I had Eclipse running before, I simply moved the "run file" (I don't know what it's called) to /usr/bin. Then when I removed the extraction folder from where I downloaded my files, the run program doesn't load properly. Am I missing something?

---

### Post by jrab227 on 2010-06-01
It got better. I found out about and ran sudo apt-get remove eclipse, then ran sudo apt-get install eclipse. Now I have eclipse installed. But where does the install occur, as in, when I run apt-get install, where is the program installed to? I also notice that I have the latest download for eclipse in my tar, and the sudo apt-get version is old, so these have nothing in common and are separate. I'm planning on running sudo apt-get remove eclipse again and I would like to know how to extract and install eclipse, and all of its contents, into its own folder in the bin.

---

### Post by HermanAB on 2010-06-01
Hmm, you will save yourself a whole lot of head-ache by consistently using the software install wizard.

First uninstall eclipse, then install it again - and use the wizard this time. (or use sudo apt-get remove yaddayadda)

---

### Post by jrab227 on 2010-06-01
true... but i'm wondering why ./configure doesn't work after I extract the tar on this distro. any suggestions?

---

### Post by 3rdalbum on 2010-06-02
> **jrab227 said:**
> true... but i'm wondering why ./configure doesn't work after I extract the tar on this distro. any suggestions?

Is your terminal navigated into the correct directory?

Do the instructions tell you to run ./configure?

Do you have the build-essential package installed?

What error message are you getting, if any?

---

### Post by jrab227 on 2010-06-02
> **3rdalbum said:**
> Is your terminal navigated into the correct directory?

Do the instructions tell you to run ./configure?

Do you have the build-essential package installed?

What error message are you getting, if any?

Yes, the read-me didn't say anything, yes, it just says ./essential doesn't exist, in that order.

Another thing that's weird is where exactly does a program's files go when I install it. Like I just installed the Java JDK from Sun and its a .bin file. after running it though, where did it go? I'm assuming the /bin is only scripts telling my computer where to get the app's files from but where is that? And if I use a tar, where does that go?

And now that I ran the .bin file, can I now remove that .bin file?

---

### Post by gandaran on 2010-06-02
use synaptic package manager to remove and install programs,its easier to manage everything than using apt-get. 
click to see properties in the installed program in synaptic, it will show you where it installed all files.

---

### Post by Zemblan on 2010-06-02
The files that are installed go to various places, binaries will go to /bin or /usr/bin, libraries /usr/lib, global config files to /etc. It's very much better to let the package manager(apt-get) or the software centre handle that sort of thing. 
A configure script can fail for a number of reasons, most probably because you are missing some component on your system that the program needs to be compiled. It is hard to help unless you include in your question the output of configure so that people can tell you exactly what has gone wrong. The package manager will take care of install all dependencies for you, which is another reason it's better to install that way, also it handles updates.

---

### Post by oldos2er on 2010-06-02
```
sudo apt-get update && sudo apt-get install build-essential
``` will give you the ability to compile source code, apart from any specific dependencies you might need.

Running Sun Java's *bin file extracts its contents to the current directory. Afterwards you need to run ```
sudo update-alternatives --install "/usr/bin/java" "java" "/directory-where-extracted/bin/java" 1

sudo update-alternatives --set java /directory-where-extracted/bin/java
```

---

### Post by sandyd on 2010-06-02
here. just do this to always get the latest version of eclipse
```

sudo apt-add-repository  ppa:eclipse-team/ppa
sudo apt-get update && sudo apt-get install eclipse && sudo apt-get upgrade
```

---

