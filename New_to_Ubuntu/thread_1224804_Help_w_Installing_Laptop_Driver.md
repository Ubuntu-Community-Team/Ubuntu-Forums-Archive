---
title: "Help w/ Installing Laptop Driver"
date: 2009-07-27
forum: New to Ubuntu
---

### Post by nickco on 2009-07-27
I own a lenovo SL400 laptop and discovered with some research that there is a driver you can install to make the volume buttons, Fn, etc, work. 

I a using a 'guide' I found [here]("http://www.thinkwiki.org/wiki/SL_Driver_on_Ubuntu") .

I have gotten as far as step 5c
> c. create a file /etc/modprobe.d/lenovo-sl-laptop.conf which just has one line: 'options lenovo-sl-laptop control_backlight=1'I can't figure out how to create a .conf file.
This is really my first experience with the terminal at all and I am learning alot, but can't figure this one out.

Thanks

---

### Post by HotShotDJ on 2009-07-27
```
touch /etc/modprobe.d/lenovo-sl-laptop.conf
```

---

### Post by niteshifter on 2009-07-27
Hi,

Just a guess here HotShot, but I'm betting the OP wants to create a file with content ;)

Create the file with the Text Editor (gedit) by typing in Terminal:
```
gksu gedit /etc/modprobe.d/lenovo-sl-laptop.conf
```
type the text in:
> options lenovo-sl-laptop control_backlight=1
and save it, exit gedit.

[what HotShot posted will not work. Two problems: permissions on /etc/modprobe.d are root:root, the touch command is not sudo'd. Second, that would be an empty file created.]

---

### Post by nickco on 2009-07-27
Thanks niteshifter, I was trying to figure out what touch was. THe problem now is I used the touch and .conf file has an orange "X" over it and says 'unknown file type' when i try to open it, and I can't delete it.

Will it still work or do I have do delete it somehow and start over?

---

### Post by niteshifter on 2009-07-28
Hi,

Yeah, let's start over. But first let's check out the file.

Get to the directory:
```
cd /etc/modprobe.d
```

List all .conf files:
```
ls -al *.conf
```

Something like the below should be output in the terminal. There may be more than one line and the date on the file will different:
```
-rw-r--r-- 1 root root [COLOR="Red"]0[/COLOR] 2009-07-27 22:42 lenovo-sl-laptop.conf
```
The number in between root and the date should be 0 (I highlighted in red in the example).
Now, if that number (it's the size of the file in bytes) **is 0**:
```
sudo rm lenovo-sl-laptop.conf
```
Will delete the file. Now you can use the command in my earlier post, and you're done.

If it wasn't 0 then do this (list the contents of the file):
```
cat lenovo-sl-laptop.conf
```
If there's anything other than what you were given to type in the file, post the output here.

[Note: Just being cautious here. Various desktop themes mask or expose visual markers as to file state. The statement about it being marked with an X (presumably in Nautilus) brought this on, as in my testing it wasn't - but I'm not using the default desktop theme. Being marked as unreadable may mean something (like it's locked) or it may mean nothing.]

---

