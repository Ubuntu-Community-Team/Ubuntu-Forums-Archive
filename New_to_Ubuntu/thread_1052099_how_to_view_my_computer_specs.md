---
title: "how to view my computer specs?"
date: 2009-01-27
forum: New to Ubuntu
---

### Post by insanity99 on 2009-01-27
like in windows iwould use dxdiag

---

### Post by overdrank on 2009-01-27
> **insanity99 said:**
> like in windows iwould use dxdiag

Hi and you can install Sysinfo or use the command in the terminal ```
lshw
```

---

### Post by OffAxis on 2009-01-27
you can also have that output an html page for easier viewing.

```
sudo lshw -html > mySpecs.html
```

---

### Post by rdmike on 2009-01-27
I don't meanto hijack this thread but I just tried pasting that command [sudo lshw -html > mySpecs.html] into my terminal and, after giving my password, all I saw was the term PCI sys and them poof nothing but the standard command prompt. Did I ere in what I entered?

---

### Post by philinux on 2009-01-27
> **rdmike said:**
> I don't meanto hijack this thread but I just tried pasting that command [sudo lshw -html > mySpecs.html] into my terminal and, after giving my password, all I saw was the term PCI sys and them poof nothing but the standard command prompt. Did I ere in what I entered?

It puts the file into your home/username folder.

---

### Post by mkvnmtr on 2009-01-27
There is an app in the package manager called sysinfo that should give you everything you need in a very easy to understand format.

---

### Post by boof1988 on 2009-01-27
> **philinux said:**
> It puts the file into your home/username folder.

I believe it puts the file in your current directory.

```

user@host:~$   # if commanad is issued from here, the file goes in user's home directory
user@host:~/Desktop$   # if command is issued from here, the file goes in user's Desktop directory
etc.

```

Please do correct me if I am wrong (or inaccurate) about this.  :p

---

### Post by stchman on 2009-01-27
> **insanity99 said:**
> like in windows iwould use dxdiag

Ubuntu has a cool app called sysinfo.

```

sudo apt-get install sysinfo

```

Then go to Applications--->System Tools--->Sysinfo

Gives you all the skinny in a nice GUI.

---

### Post by insanity99 on 2009-01-27
thanks guys quick and helpful replies as usual :D

---

### Post by spcwingo on 2009-01-27
You can also try hardinfo.  It's also in the repos.

---

### Post by MockY on 2009-01-27
> **stchman said:**
> Ubuntu has a cool app called sysinfo.

```

sudo apt-get install sysinfo

```

Then go to Applications--->System Tools--->Sysinfo

Gives you all the skinny in a nice GUI.

Bizarrely, I have never heard of this app. Very nice, though under Storage, I would like the actual size of the drive should be displayed and not just the name. It is easy to find elsewhere, but that is just my personal preference.
Thank you for the tip.

---

### Post by eb sol on 2011-05-17
**Thanks spcwingo ,, amazing app :) ..**

---

