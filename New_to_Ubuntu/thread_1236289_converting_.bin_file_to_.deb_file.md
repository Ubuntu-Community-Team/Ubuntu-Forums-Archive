---
title: "converting .bin file to .deb file"
date: 2009-08-10
forum: New to Ubuntu
---

### Post by dharanitharan on 2009-08-10
hi friends,
            I,m a new user of ubuntu 9.04... i had downloaded sun jdk which is in .bin format... to make it as installable i want to convert it as .deb file :confused:... how can i achieve that :)....


THANKS FOR YOUR HELP:)

---

### Post by benj1 on 2009-08-10
its easier to just run it.

in a terminal
'chmod +x filetochangepermissions' to make it executable

---

### Post by dje on 2009-08-10
why not just use apt?
```
sudo apt-get install sun-java6-jdk
```

---

### Post by dharanitharan on 2009-08-10
im an off line user boss... dont ve internet connection

---

### Post by dje on 2009-08-10
ah sure thing. in a terminal try:
```
sh path_to_installer.bin
```
in case you need root privileges prepend sudo:
```
sudo sh path_to_installer.bin
```

hope that helps,
dje

---

### Post by dharanitharan on 2009-08-10
actually wat s a bin fie.. wat s the diff between bin file and a deb file

---

### Post by mcduck on 2009-08-10
> **dharanitharan said:**
> actually wat s a bin fie.. wat s the diff between bin file and a deb file

a .bin file can contain any data that's in binary format (as in not text). The .bin extension dosn't tell about the type of contained data, it's just a generic extension for any binary data.

When you download a program that's distributed in .bin format the file is usually an executable program installer, much like the .exe installers used in Windows.

.deb is something completely different. It's software package used in Debian-based Linux distributions, you could pretty much think of it as some kind of advanced .zip archive that contains information about the software inside it, possible dependencies, where to extract each file inside the archive and so on. Your package manager then uses that information to extract all files into correct places in your file system.

---

### Post by dharanitharan on 2009-08-10
thanks mcduck... then how can i convert a .bin file into .rpm...

---

### Post by Arup on 2009-08-10
> **dharanitharan said:**
> thanks mcduck... then how can i convert a .bin file into .rpm...

You can't, in case you wish to install it, follow instructions noted here at [http://www.64bitjungle.com/ubuntu/install-java-jre-160-update-x-on-hardy-as-the-default-java-runtime/](http://www.64bitjungle.com/ubuntu/install-java-jre-160-update-x-on-hardy-as-the-default-java-runtime/)

---

### Post by mcduck on 2009-08-10
> **dharanitharan said:**
> thanks mcduck... then how can i convert a .bin file into .rpm...

Why would you do that?

Like already said, you can install the .bin file as it is. Converting it into anything else only makes things harder for you, and packaging software into .deb or .rpm format isn't really an easy task. (Besides, Ubuntu doesn't really even use .rpm format).

Just set the file's permissions to allow executing it, and then run the file.

For example if the file is on your desktop, the following commands would do the job:
```

cd ~/Desktop
chmod +x something.bin
./something.bin
```
(of course change the *something.bi*n into the actual file name.. :))

---

### Post by laurielegit on 2009-08-10
> **dharanitharan said:**
> actually wat s a bin fie.. wat s the diff between bin file and a deb file

.Bin files, iirc, are ok for any linux distrobution. .debs, on the other hand, are distro spesific, and only work for debian based distros such as ubuntu, knoppix, and countless others. .debs automaticaly track dependencies, and look for updates. .bins will not do this, and you will have a lot more problems.
If you say that you will not have internet acsess, why not just download a .deb from the ubuntu mirrors, shove them on a disk/mem. stick and transfer them that way. The package you want is openjdk-6-jdk, and is availible for download [here]("http://packages.ubuntu.com/jaunty/openjdk-6-jdk"). Just make sure the dependencies are installed on all the machines: the only one you're likely not to have is openjdk-6-jre openjdk-6-jre-headless.

EDIT: hmm, seems I took too long writing. I seem to be 5 posts behind

---

### Post by 3rdalbum on 2009-08-10
Asking how to convert a .bin file into a .deb or a .rpm is like asking how to convert a .exe into a .jpg.

Any file with ".bin" at the end is a program that can be run. A .deb (Debian package) is a compressed archive containing lots of files, with instructions about where those files should go and what else needs to be installed. An RPM does the same thing.

---

