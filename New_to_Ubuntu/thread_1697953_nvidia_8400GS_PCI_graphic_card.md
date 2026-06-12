---
title: "nvidia 8400GS PCI graphic card"
date: 2011-03-01
forum: New to Ubuntu
---

### Post by woodrow667 on 2011-03-01
Can anyone tell me how to blacklist the onboard intel video card? I'm trying to get my 8400GS card to work.
 
Thanks,
 
Woody

---

### Post by seawolf167 on 2011-03-01
Have you installed the latest Nvidia drivers?

[x86 driver]("http://www.nvidia.com/object/linux-display-ia32-260.19.36-driver.html")
[x86_64 driver]("http://www.nvidia.com/object/linux-display-amd64-260.19.36-driver.html")

---

### Post by MartyBuntu on 2011-03-01
Have you switched primary display adapters from the BIOS?

---

### Post by woodrow667 on 2011-03-01
> **seawolf167 said:**
> Have you installed the latest Nvidia drivers?
 
[x86 driver]("http://www.nvidia.com/object/linux-display-ia32-260.19.36-driver.html")
[x86_64 driver]("http://www.nvidia.com/object/linux-display-amd64-260.19.36-driver.html")
 
Haven't installed that driver. The os found proprietary driver for it and I activated that one. Will try this driver. Thanks.

---

### Post by woodrow667 on 2011-03-01
> **MartyBuntu said:**
> Have you switched primary display adapters from the BIOS?
 
 
Sure did. BIOS gave me the option of onboard or PCI and I switched it to PCI.

---

### Post by woodrow667 on 2011-03-01
> **seawolf167 said:**
> Have you installed the latest Nvidia drivers?

[x86 driver]("http://www.nvidia.com/object/linux-display-ia32-260.19.36-driver.html")
[x86_64 driver]("http://www.nvidia.com/object/linux-display-amd64-260.19.36-driver.html")


Got the driver downloaded to the desktop. How do I install it?

---

### Post by seawolf167 on 2011-03-01
Open a terminal (Applications -> Accessories -> Terminal)

cd to the desktop

```
cd ~/Desktop
```

make the .run executable

```
chmod +x *filenamehere*
```

run the .run file

```
./*filenamehere*
```

You'll probably get an error saying that you need to run it with superuser privileges, so then just do this instead

```
sudo ./*filenamehere*
```

---

### Post by woodrow667 on 2011-03-03
> **seawolf167 said:**
> Open a terminal (Applications -> Accessories -> Terminal)
 
cd to the desktop
 
```
cd ~/Desktop
```
 
make the .run executable
 
```
chmod +x *filenamehere*
```
 
run the .run file
 
```
./*filenamehere*
```
 
You'll probably get an error saying that you need to run it with superuser privileges, so then just do this instead
 
```
sudo ./*filenamehere*
```
 
okay, did all that and nividia setup starts to install and comes up with error that I'm running x and asked me to exit x. Don't know how to exit x. Restart brought me to a screen to a command prompt that says inframits? I had to reload Ubuntu, so I loaded the full version, still a no go. May just have to use Windows 7 because the card works with it, but win 7 is resource hungry and I love sticking it to MS any chance I get. Money hungry company. Just my honest opinion, don't want to offend anyone.:-)

---

