---
title: "Installing ndiswrapper in Lubuntu"
date: 2011-06-27
forum: New to Ubuntu
---

### Post by LokeiZero on 2011-06-27
Hello,

I am running Lubuntu and trying to install ndiswrapper-1.56 on a IBM Thinkpad 600x.

The goal is to establish an internet connection and install the drivers for either a PCI ethernet card or Wireless USB adapter.

I used the following command to extract the file:

tar zxvf ndiswrapper-1.56.tar.gz

but I am unable to run the 'make' command. I may be missing the header files, is there any way to download these for lubuntu.

It looks like my kernel version is: 2.6.38-8-generic

I got that by using the command: uname -r

---

### Post by cariboo on 2011-06-27
Ndiswrapper will only work with a wireless adapter and driver. You should be able to get a wired connection, by just plugging in the cable. Out of curiosity what is the output of:

```
lspci
```

you can create a text file of the output, that you can transfer to a system with a network connection by opening a Applications->Accessories->Terminal and issuing the following command:

```
lspci > lspci.txt
```

---

### Post by LokeiZero on 2011-06-27
> **cariboo907 said:**
> Ndiswrapper will only work with a wireless adapter and driver. You should be able to get a wired connection, by just plugging in the cable. Out of curiosity what is the output of:

```
lspci
```

you can create a text file of the output, that you can transfer to a system with a network connection by opening a Applications->Accessories->Terminal and issuing the following command:

```
lspci > lspci.txt
```

I had a feeling about the PCI adapter not working. The laptop does not have built in ethernet support and uses an unrecognized adapter: Xircom Realport Cadbus 10/100 Ethernet Adapter.

However, I have a Belkin USB wireless adapter that should hopefully work.

I tried using the command 'lspci > lspci.txt' and it just skips to the next line. Does the document output somewhere I need to search for?

---

### Post by bkratz on 2011-06-27
> **LokeiZero said:**
> I had a feeling about the PCI adapter not working. The laptop does not have built in ethernet support and uses an unrecognized adapter: Xircom Realport Cadbus 10/100 Ethernet Adapter.

However, I have a Belkin USB wireless adapter that should hopefully work.

I tried using the command 'lspci > lspci.txt' and it just skips to the next line. Does the document output somewhere I need to search for?

I believe you will find it in your home folder.

---

