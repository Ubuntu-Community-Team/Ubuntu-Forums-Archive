---
title: "How To Check MD5SUM"
date: 2011-01-23
forum: New to Ubuntu
---

### Post by daniell59 on 2011-01-23
I hate to admit it but I just cannot understand how this is done.
I would greatly appreciate it if someone could walk me through the steps. I have already downloaded Ubuntu desktop 64. I just can't understand how to make the check.

Thanks

---

### Post by Quackers on 2011-01-23
Have you seen this?
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by Elfy on 2011-01-23
In what OS?

In linux - easy

cd /location/of/iso - so if it's on the desktop

```
cd ~/Desktop
md5sum nameof.iso
```

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by Linyx on 2011-01-23
Follow the above post so that you can check all procedure..

Well, their are only two steps needed,

CD(CHANGE DIRECTORY) to the directory which contain your OS image,
then try the Command:-

```
cd /location
```
Once you change the directory to the image file, then
```
md5sum Image_name
```E.g

```
md5sum ubuntu x64.iso
```the Output will be somewhat like numbers and Alphabets e.g 
**24ea1163ea6c9f5dae77de8c49ee7c03**

[CENTER]Once you get that, copy that and visit this site > [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)
[/CENTER]
 and press Ctrl+F(for Search)
and paste that number, if that find you that number, then the Front tab will
show you which image is this, if it doesn't find anything, this means that 
your OS-IMAGE is WRONG/FAULT.

---

### Post by daniell59 on 2011-01-23
Thanks, I should have mentioned Ubuntu 10.10 64

---

### Post by Elfy on 2011-01-23
Doesn't matter the name of the iso - the way to check is the same

md5sum ridiculouslylongandpointlessyinaneisoname.iso

post #4 has a link to all the current ubuntu image hash numbers

---

### Post by daniell59 on 2011-01-23
Please excuse another inane question. I am trying to learn.
The Ubuntu download is in my download directory. How do I write the correct path? I tried CD /director and it could not find it. Obviously I need to put in the path.

Thanks again.

---

### Post by Elfy on 2011-01-23
If it's the default download directory then 

```
cd Downloads
```

if you are at your home in the terminal 

if not then ```
cd ~/Downloads
```will get you there from anywhere (~/ being a shortcut to your /home

---

### Post by daniell59 on 2011-01-23
Again I am experiencing some difficulty. 
Please see screen shot.

---

### Post by kevdog on 2011-01-23
Did you install the package coreutils?

sudo aptitude install coreutils

---

### Post by daniell59 on 2011-01-23
> **kevdog said:**
> Did you install the package coreutils?

sudo aptitude install coreutils

Please explain what this package is.

Thanks

---

### Post by Elfy on 2011-01-23
TRy using md5sum not mdsum ;)

---

### Post by daniell59 on 2011-01-23
> **forestpiskie said:**
> TRy using md5sum not mdsum ;)

Did so and got the following error. md5sum ubuntu-9.10-desktop-amd64(2).iso
bash: syntax error near unexpected token `('

Maybe I am copying the name wrong.

---

### Post by daniell59 on 2011-01-23
I changed the download name to an easier to type name. This time it generated a number. All that remains is for me to locate the number and compare. Thanks to all for your kind and informative assistance.

---

### Post by CharlesA on 2011-01-23
> **daniell59 said:**
> I changed the download name to an easier to type name. This time it generated a number. All that remains is for me to locate the number and compare. Thanks to all for your kind and informative assistance.
Yep. The "()" can cause problems sometimes.

See here for the hashes: [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

---

### Post by daniell59 on 2011-01-23
Checked number and found it to be perfect.

---

