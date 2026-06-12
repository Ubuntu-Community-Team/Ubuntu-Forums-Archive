---
title: "How to unlock a file"
date: 2011-05-26
forum: New to Ubuntu
---

### Post by bj218 on 2011-05-26
How do I remove the lock on a scanned file?

---

### Post by sanguinoso on 2011-05-26
Can you post the output of ```
ls -al your_file.pdf
```

---

### Post by spillage2 on 2011-05-26
sure sudo chown username /file/location/ should give the user permission..

---

### Post by bj218 on 2011-05-26
> **sanguinoso said:**
> Can you post the output of ```
ls -al your_file.pdf
```

I think this is what you wanted.

---

### Post by audiomick on 2011-05-26
You could try starting Nautilus with root privileges and changing the ownership.

To do this:

```
gksu nautlius
```

The instance of Nautilus that starts with that command can do anything, so be careful with it, and close it again as soon as you have done what you want.

In that, right click on the file and choose "properties". One of the tabs is "permissions" or something like that. In there, you should be able to take ownership of the file, or allow everyone to get at it.

---

### Post by bj218 on 2011-05-26
> **spillage2 said:**
> sure sudo chown username /file/location/ should give the user permission..

I don't think I did this wright
bill@bill-desktop:~$ sudo chown bj218/'/home/bill/2bj52612.pdf' 
[sudo] password for bill: 
chown: missing operand after `bj218//home/bill/2bj52612.pdf'
Try `chown --help' for more information.
bill@bill-desktop:~$ sudo chown bj218/home/bill/2bj52612.pdf
chown: missing operand after `bj218/home/bill/2bj52612.pdf'
Try `chown --help' for more information.
bill@bill-desktop:~$  sudo chown bj218/file/home/bill/2bj52612.pdf
chown: missing operand after `bj218/file/home/bill/2bj52612.pdf'
Try `chown --help' for more information.
bill@bill-desktop:~$

---

### Post by audiomick on 2011-05-26
I think you are missing a space between your user name and the file name.

Try the "nautilus with root privileges" method. I find it easier to understand... ;)

---

### Post by AlphaLexman on 2011-05-26
In your [COLOR="Red"]first[/COLOR] post you have a screenshot of a file with the name '**2bj52612.pdf**' with with a padlock and X attributes on the icon.

In your [COLOR="red"]second[/COLOR] post you have a screenshot of a file with the name '**screenshot.png**' with -rw-r--r-- permissions.

You are comparing Apples to Oranges with two different files. Which file are you trying to gain access to.?

---

### Post by AlphaLexman on 2011-05-26
Audiomick was quicker than me on many levels...

Try this:
```
sudo chown 644 ~/2bj52612.pdf
```

---

### Post by audiomick on 2011-05-26
:P

That should work too. ;)

---

### Post by bj218 on 2011-05-26
> **AlphaLexman said:**
> In your [COLOR="Red"]first[/COLOR] post you have a screenshot of a file with the name '**2bj52612.pdf**' with with a padlock and X attributes on the icon.

In your [COLOR="red"]second[/COLOR] post you have a screenshot of a file with the name '**screenshot.png**' with -rw-r--r-- permissions.

You are comparing Apples to Oranges with two different files. Which file are you trying to gain access to.?

Both files are pdf!!  png is a screenshot extension!!

---

### Post by audiomick on 2011-05-26
> **bj218 said:**
> Both files are pdf!!  png is a screenshot extension!!
Whatever...

Have you tried the "chown" from AlphaLexman or the "gksu nautilus" to take possession of the file that is giving you trouble?

---

### Post by AlphaLexman on 2011-05-26
> **bj218 said:**
> Both files are pdf!!  png is a screenshot extension!!
I know the difference,... in your second post the screenshot shows the output of:
```
ls -al /home/bill/Desktop/screenshot.png
```
Which is **NOT** *.pdf file!

**EDIT:** Audiomick was quicker than me **AGAIN!**

---

### Post by wojox on 2011-05-26
```
sudo chmod 777 2bj52612.pdf
```

---

### Post by bj218 on 2011-05-27
> **wojox said:**
> ```
sudo chmod 777 2bj52612.pdf
```

Fop just a moment I thought I had a solution but no such luck.Can you tell me what I did wrong on the second file?

bill@bill-desktop:~$ sudo chmod 777 2bj52612.pdf
[sudo] password for bill: 
bill@bill-desktop:~$  sudo chmod 777 2bj52612.pdf
bill@bill-desktop:~$  sudo chmod 777 2bj52612.pdf
bill@bill-desktop:~$ sudo chmod 777 2bj52611.pdf
chmod: cannot access `2bj52611.pdf': No such file or directory
bill@bill-desktop:~$ sudo chmod 777 2bj52611.pdf
chmod: cannot access `2bj52611.pdf': No such file or directory
bill@bill-desktop:~$ 
The lock on the first file has been removed ie  2bj52612 but not on the second one ie 2bj52611 why.

---

### Post by wojox on 2011-05-27
Are you sure that's the name of the second file? In the first picture it's **bj52611.pdf**. :p

---

### Post by bj218 on 2011-05-27
> **wojox said:**
> Are you sure that's the name of the second file? In the first picture it's **bj52611.pdf**. :p

How dumb when I put it in correctly it worked!! THANKS TO ALL. I hope I 
learned a few things from this??

---

### Post by audiomick on 2011-05-27
> **bj218 said:**
> How dumb when I put it in correctly it worked!! THANKS TO ALL. I hope I 
learned a few things from this??


You're welcome. If you want to consolidate your learning a bit, do

```
man chmod
```

and

```
man chown
```

in a terminal, and have a look at what shows up. The command "man" opens the manual for the command that follows, so "man chmod" opens the manual for the command "chmod", which you seem to have just used.

---

