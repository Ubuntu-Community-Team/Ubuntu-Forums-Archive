---
title: "Can't unrar anything. Please Help!"
date: 2011-03-24
forum: New to Ubuntu
---

### Post by pyrodude8 on 2011-03-24
I've tried several downloads and I doubt all of them were corrupt.

p, li { white-space: pre-wrap; } Reading the archive '/home/drock/AntiWPA.rar' failed with the error 'Failed to locate program 'unrar' in PATH.'
This is the message that shows up whenever I try. Am I missing a program or something. Haven't found one in different directories and honestly I'm not sure what I'm looking for. Advice would be greatly appreciated.

I'm running a custom built computer running Kubuntu 10.10 and a hard drive with Windows xp
AMD phenom II Quad Core
Asus M2N68 LM plus

---

### Post by Perfect Storm on 2011-03-24
Did you installed unrar?

---

### Post by SeijiSensei on 2011-03-24
RAR has patent limitations and can't be included in the default distribution.  It's in the [multiverse]("http://packages.ubuntu.com/lucid/unrar") repository.

---

### Post by seawolf167 on 2011-03-24
You can also use 7zip

```
sudo apt-get install p7zip-full
```

I've had some problems with extracting multipart files if they were created in Windows, so I had to start using 7z

```
man 7z
```

---

### Post by pyrodude8 on 2011-03-24
Wow thanks for the speedy response! I figured it hadn't been included. 
Now that I know what programs to look for I should be able to get this sorted out.

Thanks again!:P

---

