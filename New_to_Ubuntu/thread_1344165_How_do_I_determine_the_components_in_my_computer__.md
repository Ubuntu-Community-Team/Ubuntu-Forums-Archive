---
title: "How do I determine the components in my computer?  Ubuntu finds them automatically"
date: 2009-12-02
forum: New to Ubuntu
---

### Post by wildbill46 on 2009-12-02
Noob here.  I'm having setting up a dual boot system.  Koala finds the devices and sets up the drivers automatically.  However, windows doesn't find the ethernet card, video card or sound card drivers.  How do I determine what these devices are so I can download the windows drivers. This is a "garage sale" 'puter that I'm just playing with.

Thanks in advance,
Bill

---

### Post by NoaHall on 2009-12-02
Inside windows 
Start -> Run(or control panel) -> Device Manager

---

### Post by SuperSonic4 on 2009-12-02
> **NoaHall said:**
> Inside windows 
Start -> Run(or control panel) -> Device Manager

Inside Linux

```
lspci > devices.txt
```

That will pipe it to a text file called devices which can be opened in windows

---

### Post by NoaHall on 2009-12-02
> **SuperSonic4 said:**
> Inside Linux

```
lspci > devices.txt
```

That will pipe it to a text file called devices which can be opened in windows

Or ```
sudo apt-get install hardinfo && hardinfo
```
Will give you a graphical interface to that information & more. Will only work in Ubuntu though, but I think you can export the data from it to a .html file or .txt.

---

### Post by halitech on 2009-12-02
I'm guessing you want to use Ubuntu to figure out the hardware so you can find the windows drivers. This may or may not work very well but you can try
```
lspci -v
```

You can also install hardinfo and run hardinfo to get info.
```
sudo apt-get install hardinfo
```

---

### Post by vambo on 2009-12-02
```
sudo lshw
```

Will give you everything you need to know - and some you perhaps don't.
Might be best to send it to a file, eg

```
sudo lshw > hw.txt
```

---

### Post by wildbill46 on 2009-12-02
Thanks a bunch guys.  I've got it working now.  Have a great day.:D

---

