---
title: "Need help with MD5sum, please."
date: 2010-01-29
forum: New to Ubuntu
---

### Post by L Campbell on 2010-01-29
I have the ubuntu-8.04.4-desktop-i386.iso on my desktop but when I try to get the MD5sum for it, I get this message:-

qwer@qwer-desktop:~$ md5sum ubuntu-8.04.4-desktop-i386.iso
md5sum: ubuntu-8.04.4-desktop-i386.iso: No such file or directory

I would appreciate your help here

TIA

---

### Post by Mornedhel on 2010-01-29
This seems to be confusing for new users, but when you start a terminal, the default working directory is not the Desktop. Instead, it's the user's home directory (indicated by the tilde "~"). The user's Desktop is in the home directory, so you need to

```
cd Desktop
```

first. Then you should be able to see the files stored there.

---

### Post by Rex Bouwense on 2010-01-29
You probably downloaded 8.04 to your downloads, which probably is a directory inside of documents.  Anyway see [https://help.ubuntu.com/community/HowToMD5SUM#Check%20the%20iso%20file](https://help.ubuntu.com/community/HowToMD5SUM#Check%20the%20iso%20file).  
That should help you out.

---

### Post by tom.swartz07 on 2010-01-29
> **L Campbell said:**
> I have the ubuntu-8.04.4-desktop-i386.iso on my desktop but when I try to get the MD5sum for it, I get this message:-

qwer@qwer-desktop:~$ md5sum ubuntu-8.04.4-desktop-i386.iso
md5sum: ubuntu-8.04.4-desktop-i386.iso: No such file or directory

I would appreciate your help here

TIA

The easiest way to make sure that you have the correct thing is to hit TAB 

for example, change your directory to Desktop
```
cd Des<TAB>
```
will give you 
```
cd /home/username/Desktop/
```

Same applies to your md5sum
```
md5sum ubu<TAB>
```
should complete it to your file. If it doesnt, then somethings wrong.

---

### Post by L Campbell on 2010-01-29
> **Mornedhel said:**
> This seems to be confusing for new users, but when you start a terminal, the default working directory is not the Desktop. Instead, it's the user's home directory (indicated by the tilde "~"). The user's Desktop is in the home directory, so you need to

```
cd Desktop
```

first. Then you should be able to see the files stored there.

Thanks, frankly I'm still confused but it worked.

4f41e03d250b2f2b1cd3015c8df4af7c 

I appreciate the help.

---

### Post by SoftwareExplorer on 2010-01-29
When you press tab in the terminal, it tries to guess what you are going to type from what you already typed and puts it in for you. It guesses from what would be the valid options for you to type, so it's a good way to make sure that the folder you are trying to change to actually exists. 
The 'cd' command changes the directory (folder) the terminal is running in. So when you type cd <TAB> it will try to guess from what folders are in the folder you are currently in. You you can also list the files in the current folder with the command ```
ls
```.

---

### Post by tom.swartz07 on 2010-01-29
> **L Campbell said:**
> Thanks, frankly I'm still confused but it worked.

4f41e03d250b2f2b1cd3015c8df4af7c 

I appreciate the help.

Do you know how to compare them?
If you check the ubuntu site, theres a list of checksums for each download.

you compare this long string of numbers to the checksum you get after you finish downloading it to make sure that you have a 'full download'. Sometimes the download has errors (theres a lot of chances for it to get one)

Anyway- according to this site: [http://releases.ubuntu.com/hardy/MD5SUMS](http://releases.ubuntu.com/hardy/MD5SUMS)

4f41e03d250b2f2b1cd3015c8df4af7c *ubuntu-8.04.4-desktop-i386.iso
Should be the checksum you get, and it looks like everything is all clear!

---

### Post by L Campbell on 2010-01-29
> **tom.swartz07 said:**
> Do you know how to compare them?
If you check the ubuntu site, theres a list of checksums for each download.

you compare this long string of numbers to the checksum you get after you finish downloading it to make sure that you have a 'full download'. Sometimes the download has errors (theres a lot of chances for it to get one)

Anyway- according to this site: [http://releases.ubuntu.com/hardy/MD5SUMS](http://releases.ubuntu.com/hardy/MD5SUMS)

4f41e03d250b2f2b1cd3015c8df4af7c *ubuntu-8.04.4-desktop-i386.iso
Should be the checksum you get, and it looks like everything is all clear!

Thanks for taking the time to write such a clear explanation.

Kind regards.

---

### Post by egalvan on 2010-01-29
I downloaded these Nautilus scripts back in m Hardy days.
"Open Terminal Here" is one of the scripts.
Just highlight a file or directory, right-click and "open a terminal there". It' a great time saver.

And the pack also includes a "Show md5sum" script.

[http://www.ubuntu-unleashed.com/2007/09/125-nautilus-scripts-to-simplify.html](http://www.ubuntu-unleashed.com/2007/09/125-nautilus-scripts-to-simplify.html)


note: these scripts do nothing to hone your command-line skills :)
but they sure are handy!

---

### Post by tom.swartz07 on 2010-01-29
> **L Campbell said:**
> Thanks for taking the time to write such a clear explanation.

Kind regards.

Sure! Thats what we're here for, after all! :P

Enjoy!

---

