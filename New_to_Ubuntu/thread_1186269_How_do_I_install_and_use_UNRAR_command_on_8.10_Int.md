---
title: "How do I install and use UNRAR command on 8.10 Intrepid"
date: 2009-06-13
forum: New to Ubuntu
---

### Post by Ubunser on 2009-06-13
apt-get install unrar

After using this command it asks if I am root
But don't know how to run it as root

---

### Post by howefield on 2009-06-13
I think it is simply a case of installing via synaptic or using the terminal command

```
sudo apt-get install rar
```

The functionality will then be available to file-roller (archive manager)

---

### Post by gradinaruvasile on 2009-06-13
Applications->Add/Remove

Select "All available applications" from the upper drop down list
type "rar" in the search box
wait
tick "RAR"
click "Apply Changes"
After that you can unpack files with the ubuntu default archive manager

I personally like 7zip more... Can be installed exactly the same way (you should btw, to be able to open 7z archives and a wide variety of other supported ones)

Damn i was beaten at it..

---

### Post by howefield on 2009-06-13
> **Ubunser said:**
> apt-get install unrar

After using this command it asks if I am root
But don't know how to run it as root

Prefix your command with sudo

Then when it asks, type your password and press enter, (you will not see your password being typed)

---

### Post by Ubunser on 2009-06-13
Before I saw your replies I typed:

$ cd /tmp
$ wget [http://www.rarlab.com/rar/rarlinux-3.6.0.tar.gz](http://www.rarlab.com/rar/rarlinux-3.6.0.tar.gz)

It installed something. But when I tried to use it by moving to the needed directory and typig:

unrar e file.rar

it responded:

The program 'unrar' can be found in the following packages:
 * unrar-free
 * unrar
Try: sudo apt-get install <selected package>
bash: unrar: command not found
talkthee@talkthee-desktop:~/Desktop$ 


Help

---

### Post by whoop on 2009-06-13
> **Ubunser said:**
> Before I saw your replies I typed:

$ cd /tmp
$ wget [http://www.rarlab.com/rar/rarlinux-3.6.0.tar.gz](http://www.rarlab.com/rar/rarlinux-3.6.0.tar.gz)

It installed something. But when I tried to use it by moving to the needed directory and typig:

unrar e file.rar

it responded:

The program 'unrar' can be found in the following packages:
 * unrar-free
 * unrar
Try: sudo apt-get install <selected package>
bash: unrar: command not found
talkthee@talkthee-desktop:~/Desktop$ 


Help
sudo apt-get install unrar

---

### Post by gradinaruvasile on 2009-06-13
The program 'unrar' can be found in the following packages:
* unrar-free
* unrar
[COLOR="Red"]Try: sudo apt-get install <selected package>[/COLOR]
bash: unrar: command not found

There you have it... replace it with unrar.

In ubuntu 9.04 the rar version is 3.80 ... no need to install stuff like that. I dont know exactly what rar version is, but should be at least 3.60...

That file u have there is a console version too... If u have it in ubuntu, u should use it because of better integration.

---

### Post by Ubunser on 2009-06-13
> **whoop said:**
> sudo apt-get install unrar

it was installed, then I tried to use it like before and it worked as well. But thelast question is:

&#1090;&#1080;&#1090;&#1091;&#1083;.doc already exists. Overwrite it ?
[Y]es, [N]o, [A]ll, n[E]ver, [R]ename, [Q]uit N   

Is this bad?

---

### Post by gradinaruvasile on 2009-06-13
> **Ubunser said:**
> it was installed, then I tried to use it like before and it worked as well. But thelast question is:

&#1090;&#1080;&#1090;&#1091;&#1083;.doc already exists. Overwrite it ?
[Y]es, [N]o, [A]ll, n[E]ver, [R]ename, [Q]uit N   

Is this bad?
No. It asking about a .doc (text file to replace. Probably you never need it for anything....

---

### Post by whoop on 2009-06-13
> **Ubunser said:**
> it was installed, then I tried to use it like before and it worked as well. But thelast question is:

&#1090;&#1080;&#1090;&#1091;&#1083;.doc already exists. Overwrite it ?
[Y]es, [N]o, [A]ll, n[E]ver, [R]ename, [Q]uit N   

Is this bad?

It means there is already a document with the same name in the location you are extracting the rar file to (so the rar holds a document with the same name).

So it's not bad at all (unless the doc on your hd is useful and the doc in the rar is useless and you choose to overwrite).

---

### Post by colau on 2009-08-15
> **Ubunser said:**
> it was installed, then I tried to use it like before and it worked as well. But thelast question is:

&#1090;&#1080;&#1090;&#1091;&#1083;.doc already exists. Overwrite it ?
[Y]es, [N]o, [A]ll, n[E]ver, [R]ename, [Q]uit N   

Replace.
> 
Is this bad?
No.

---

### Post by ad_267 on 2009-08-15
You don't have to use unrar from the command line. You can right click on a file and select "extract".

---

