---
title: "ATI Drivers"
date: 2009-02-07
forum: New to Ubuntu
---

### Post by Lex-Man on 2009-02-07
How would I go about installing the ATI priority drivers from the ATI/AMD website?  

I have downloaded the latest version as a run file to my desktop, how do I run it?

---

### Post by billgoldberg on 2009-02-07
If I were you I would use the program

Envy NG

google it.

It's a lot easier than doing a manual install.

---

### Post by CowzRule on 2009-02-07
[Unofficial Wiki for the ATI Linux Driver]("http://wiki.cchtml.com/index.php/Ubuntu")

---

### Post by blueridgedog on 2009-02-07
Go to System -> Administration -> Hardware Drives and you can install the latest Ubuntu approved proprietary hardware driver.

---

### Post by Bablefish on 2009-02-07
But please becareful if Envy doesn't work. I had a bad experiance trying to install Linux ATI drivers. My OS crashed.

---

### Post by Alterax on 2009-02-07
> **blueridgedog said:**
> Go to System -> Administration -> Hardware Drives and you can install the latest Ubuntu approved proprietary hardware driver.

That's the easier, this is true.  But he was asking how to run the installer from AMD/ATI's site.

So here goes:  Before installing, make sure to get the kernel source code and essential build utilities, because the installer uses these to build the driver for your machine.  Do that from the terminal like this:

```
sudo apt-get install linux-source build-essential
```

once those are done, you can use the cd command to get to the directory that you have the installer script in.  There is a flag that needs to be set on the file to make it executable:  

```
chmod a+x whatever_the_amd_filename_is.sh 
```

Note that it's usually a lot easier to get these strange filenames right by typing the first couple of letters in the name, then using the TAB key to autocomplete.  

Then you'll need to run the script as root.

```
sudo ./whatever_the_amd_filename_is.sh
```

The ./ before the filename just lets the terminal/shell know that you want to run the file that is in THIS directory.

It may have a couple of questions for you, but that's about it.  One thing I've observed though is that the ATI drivers have had some trouble with the past with the ability to handle compositing.  The open-source drivers that came with Intrepid didn't seem to have this problem, so if ATI's driver doesn't perform that well, you may want to give the Open-Source drivers a try.

have fun!

---

### Post by blueridgedog on 2009-02-07
> **Alterax said:**
> That's the easier, this is true.  But he was asking how to run the installer from AMD/ATI's site.



My point was that there is little to be gained in getting the driver from AMD.  It is not substantially different than the one that can be installed by a few clicks and then easily updated as new releases are folded into the Ubuntu tree.  Your advice and method are great though.

---

