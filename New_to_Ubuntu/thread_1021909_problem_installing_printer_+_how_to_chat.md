---
title: "problem installing printer + how to chat?"
date: 2008-12-26
forum: New to Ubuntu
---

### Post by RajaAjmal on 2008-12-26
_1st problem_
i've samsung printer model scx4521f together with its driver. i've read the 'readme' file given with the driver - it says to log in as a super user, go to the location where the driver is located and type './install.sh' . but when do so, i get the following problems.

[B]root@raja-desktop:~/Desktop/Linux# ./install.sh
./install.sh: 11: source: not found
[: 670: ==: unexpected operator[/B]

and when try it without being super user, i get the following error msg.raja@raja-desktop:~/Desktop/Linux$ ./install.sh
./install.sh: 11: source: not found
cp: cannot remove `/usr/local/bin//x86_64/Configurator': Permission denied
cp: cannot remove `/usr/local/bin//x86_64/libGDI.so.1.0.0': Permission denied
cp: cannot remove `/usr/local/bin//x86_64/libmfp.so.1.0.1': Permission denied
cp: cannot remove `/usr/local/bin//x86_64/libmfpdetect.so.1.0.1': Permission denied
cp: cannot remove `/usr/local/bin//x86_64/libsane-samsung_mfp560.so.1.0.1': Permission denied
cp: cannot remove `/usr/local/bin//x86_64/libsane-samsung_mfp750.so.1.0.1': Permission denied
cp: cannot remove `/usr/local/bin//x86_64/libsane-samsung_scx4100.so.1.0.1': Permission denied
cp: cannot remove `/usr/local/bin//x86_64/libsane-samsung_scx4x16.so.1.0.1': Permission denied
cp: cannot remove `/usr/local/bin//x86_64/libsane-samsung_scx4x20.so.1.0.1': Permission denied
cp: cannot remove `/usr/local/bin//x86_64/libsane-samsung_scx4x21.so.1.0.1': Permission denied
cp: cannot remove `/usr/local/bin//x86_64/libsane-samsung_scx5312f.so.1.0.1': Permission denied
cp: cannot remove `/usr/local/bin//x86_64/libsane-samsung_scx6x20.so.1.0.1': Permission denied
cp: cannot remove `/usr/local/bin//x86_64/libsane-samsung_sf531p.so.1.0.1': Permission denied
cp: cannot remove `/usr/local/bin//x86_64/mfp': Permission denied
cp: cannot remove `/usr/local/bin//x86_64/modules.tgz': Permission denied
cp: cannot remove `/usr/local/bin//x86_64/rastertosamsungpcl': Permission denied
cp: cannot remove `/usr/local/bin//x86_64/rastertosamsungspl': Permission denied
cp: cannot remove `/usr/local/bin//x86_64/slpr': Permission denied
cp: cannot remove `/usr/local/bin//x86_64/slprhelper': Permission denied
[: 670: ==: unexpected operator

_2nd problem_
how to chat online with #ubuntu ?
what software to use to chat with #ubuntu?
when installing ubuntu, does it already have a chat software or i need to download and install one?

---

### Post by RomeReactor on 2008-12-26
Hi. Does this also happen running the command using **sudo**?:
```
sudo ./install.sh
```
Can you provide a link to get the driver?

As for chatting in #ubuntu, you can use Pidgin, which is already installed in your system and is located in 'Applcations->Internet->Pidgin'.

---

### Post by RajaAjmal on 2008-12-26
thanks romereactor.
even when trying 'sudo ./install.sh', i got the same error msg as when root.
the driver, i did not download it. it comes with the printer when purchase it.

+ thnks for informing me about the Pidgin.

---

### Post by nhasian on 2008-12-26
xchat is a very good irc client.  

```
sudo apt-get install xchat
```

---

### Post by RajaAjmal on 2008-12-26
thanks romereactor.
even when trying 'sudo ./install.sh', i got the same error msg as when root.
the driver, i did not download it. it comes with the printer when purchase it.

+ thnks for informing me about the Pidgin.

---

### Post by alienexplorers on 2008-12-26
Are you running 32 or 64 bit Ubuntu?

---

### Post by RomeReactor on 2008-12-26
Did you copy the driver to your PC or are you running it from the disc? Are you running 64 bit Ubuntu?

---

### Post by RajaAjmal on 2008-12-27
i copy the driver on my desktop and installed it from there. and for the 64 bit ubuntu, i don't know. how to know?
i'm using ubuntu 8.04 hardy heron.
my pc consists of a dual core processor.

---

### Post by RomeReactor on 2008-12-27
Please open the driver in a text editor and post the first line. If it reads:
```
#!/bin/sh
```
change it to:
```
#!/bin/bash
```
and try it again.

To find out if you have Ubuntu 64 bit, run:
```
uname -m
```
If it returns **x86_64**, you have Ubuntu 64 bit. If it's **i686**, it's 32 bit. However, I don't think it matters; it appears the driver can be installed on both architectures.

---

### Post by RajaAjmal on 2008-12-27
thanks for your help romeReactor. i've been be able to find a website where it specifies how to install samsung printer scx4521f. i'll try it and hope that it works.
by the way i've tried what you've said.
i've changed the #!/bin/sh to #!/bin/bash. but in doing so, i can only saved the document with a different name. so i've named it as install1.sh. and when i run it, i get this error msg
[B]bash: ./install1.sh: Permission denied
[/B]


also my ubuntu is 32bit. can you pls tel me  what that meant- ubuntu 64 bit or ubuntu32 bit?

---

### Post by RajaAjmal on 2008-12-27
thanks for your help romeReactor. i've been be able to find a website where it specifies how to install samsung printer scx4521f. i'll try it and hope that it works.
by the way i've tried what you've said.
i've changed the #!/bin/sh to #!/bin/bash. but in doing so, i can only saved the document with a different name. so i've named it as install1.sh. and when i run it, i get this error msg
[B]bash: ./install1.sh: Permission denied
[/B]


also my ubuntu is 32bit. can you pls tel me  what that meant- ubuntu 64 bit or ubuntu32 bit?

---

### Post by RomeReactor on 2008-12-27
> **RajaAjmal said:**
> i've changed the #!/bin/sh to #!/bin/bash. but in doing so, i can only saved the document with a different name.
This is likely because the driver didn't give permission to edit it, you saved a text file that was not executable. You can try this:

To avoid navigating to the file's location from the terminal, move the *original* **install.sh** file to your desktop; then, from the terminal, run:
```
gksudo gedit ~/Desktop/install.sh
```
Now you can edit it and save it, then return it to its original folder, where you can run it again.


> also my ubuntu is 32bit. can you pls tel me  what that meant- ubuntu 64 bit or ubuntu32 bit?

32 bit or 64 bit refers to the architecture of the processor or the operating system; normally, 32 bit processors and operating systems can only access just under 3 GB of RAM, while 64 bit systems can use much more. 64 bit systems can also perform much better on processor-intensive tasks, such as video encoding and some mathematical operations.

Sorry for the late replies.

---

### Post by Firestone on 2008-12-27
You can make the sh file executable(for root) by giving the following command:
```
sudo chmod 744 install1.sh
```

Then try it again.

---

