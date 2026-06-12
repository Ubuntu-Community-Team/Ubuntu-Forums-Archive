---
title: "Can someone explain how I go about compiling kernels?"
date: 2009-03-22
forum: New to Ubuntu
---

### Post by Awesomeist on 2009-03-22
Hello all! Any help is much appreciated.

Basically, I'm currently on a laptop which has had a few various problems, and as a result, I can no longer install windows on it, so I thought I'd give Ubuntu a try.

This is whole new territory to me, and I just noticed how some of my hardware doesn't work. More specifically, my Ricoh SD/MMC/XD Card Reader.

Sure, I've googled and it says that I need to compile a kernel in order for it to work, and I've looked around for information on that, but it still makes no sense!

If anyone could explain how I got about installing this card reader, it would be much appreciated.

Thanks!

---

### Post by LiamWilson on 2009-03-22
Whoah, you don't need to do that, not yet. We can just get your Card Reader to work without such hassle. Is it a USB one, yes?

---

### Post by Awesomeist on 2009-03-22
No it is an internal card reader.
If it helps, the laptop's build is: Dell Inspiron 6400

---

### Post by LiamWilson on 2009-03-22
Do they appear in ```
dmesg | tail
```

---

### Post by Awesomeist on 2009-03-22
Um, I'm afraid I don't know what you mean.

As I said, I'm fresh off of Windows, this is my first time using Linux, so I'm lacking essential knowledge.

---

### Post by drowner on 2009-03-22
type that in to a terminal:

```
dmesg | tail
```

Does it appear there? If you can't tell, just copy the output here

---

### Post by nothingspecial on 2009-03-22
I`m guessing [[COLOR="Red"]these[/COLOR]]("http://mydebian.blogdns.org/?p=243") are the instructions you are following.

They are not about compiling your own kernel, they are about compiling a module which is the linux term for driver.

[COLOR="Red"][SIZE="5"]I have no idea how safe this is - do it at your own risk[/SIZE][/COLOR]

Download the file. Extract it where ever you like but for an example your Desktop.

Now you need to open a terminal (accessories > terminal) in your menu and go to your Desktop. Type ```
cd Desktop
```

Then copy and paste the lines in the instructions one at a time.

---

### Post by nothingspecial on 2009-03-22
You also need to get into the file you just downloaded

```
cd sdricoh_cs-0.1.4
```

Just the four lines

```
sudo apt-get install build-essential
```

This is installing software that allows you to compile source code (amongst other things)

```
make
```

```
sudo make install
```

Those 2 lines compile the module (driver)

```
sudo modprobe sdricoh_cs
```

That loads the module (driver)

---

### Post by Awesomeist on 2009-03-22
Well, I can't tell, but this is what came up.

```
[ 3568.644800] end_request: I/O error, dev mmcblk0, sector 255
[ 3568.644812] end_request: I/O error, dev mmcblk0, sector 256
[ 3568.644819] end_request: I/O error, dev mmcblk0, sector 257
[ 3568.644829] end_request: I/O error, dev mmcblk0, sector 258
[ 3568.644835] end_request: I/O error, dev mmcblk0, sector 259
[ 3568.644841] end_request: I/O error, dev mmcblk0, sector 260
[ 3568.644848] end_request: I/O error, dev mmcblk0, sector 261
[ 3568.644856] end_request: I/O error, dev mmcblk0, sector 262
[ 4590.246505] __ratelimit: 62 callbacks suppressed
[ 4590.246520] gnome-screensav[10126]: segfault at 200 ip b8047fed sp bfa510a0 error 4 in ld-2.8.90.so[b8035000+1a000]

```

EDIT: This is in response to drowner, trying out the download now.

---

### Post by Awesomeist on 2009-03-22
It all works now! Thanks very much!

---

### Post by nothingspecial on 2009-03-22
Cool.

---

