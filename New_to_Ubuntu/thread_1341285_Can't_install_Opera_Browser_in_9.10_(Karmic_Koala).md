---
title: "Can't install Opera Browser in 9.10 (Karmic Koala)"
date: 2009-11-29
forum: New to Ubuntu
---

### Post by syeef on 2009-11-29
I can't install Opera Browser using this code
```
sudo apt-get install opera
```I download a 12.8 MB *.tar.gz file from [http://www.opera.com/browser/download/](http://www.opera.com/browser/download/)
I extract the files and run the install.sh file in terminal, then i see in terminal
```

Files shall be installed as follows:
-----------------------------------------------------------
 Wrapper Script : /home/syeef/bin
 Binaries       : /home/syeef/lib/opera/10.10
 Plugins        : /home/syeef/lib/opera/plugins
 Shared files   : /home/syeef/share/opera
 Documentation  : /home/syeef/share/doc/opera
 Manual page    : /home/syeef/share/man
-----------------------------------------------------------
Is this correct [ y,n,c | yes,no,cancel ] ?
```I press "Y" and Enter. I see some lines creating in listed rapidly and auto close the terminal. It happens too quickly to read/copy/ScreenShot.
Now please tell how to run Opera. i can't see opera in Applications>Internet

I'm a new Ubuntu User. If i wrote anything wrong please don't mind.
Thank You all.

---

### Post by kellemes on 2009-11-29
Better use the Opera repository..
[https://help.ubuntu.com/community/OperaBrowser]("https://help.ubuntu.com/community/OperaBrowser")

---

### Post by Virtual Liberty on 2009-11-29
> **syeef said:**
> I can't install Opera Browser using this code
```
sudo apt-get install opera
```

[ snip ]

---

### Post by kellemes on 2009-11-29
> **Virtual Liberty said:**
> Would be nice if you could tell us a little bit more about this. Why it is so that you can't install from Ubuntu repositories ?

Because Opera isn't available in the Ubuntu repositories.

---

### Post by chickengirl on 2009-11-29
Try typing "opera" in a terminal. If opera is installed, that should launch it.

---

### Post by Virtual Liberty on 2009-11-29
> **kellemes said:**
> Because Opera isn't available in the Ubuntu repositories.

Eh .. Mint 8-[

---

### Post by syeef on 2009-11-29
Thanks **kellemes** for the link. :P

Some folder was created (bold named below) at my home folder.

/home/syeef/lib/**opera/10.10**
/home/syeef/lib/**opera/plugins**
/home/syeef/share/**opera**
/home/syeef/share/**doc/opera**

I think my previous downloaded file was installed. am i right?
To remove that is find opera in Applications>Ubuntu Software Center and
System>Administration>Synaptic Package Manager

Now how to uninstall (if already installed) my previously download opera.

---

### Post by syeef on 2009-11-29
> **chickengirl said:**
> Try typing "opera" in a terminal. If opera is installed, that should launch it.
i did, see the result below (copied from terminal)
```
syeef@syeef-desktop:~$ opera
/home/syeef/bin/opera: 4: Syntax error: "(" unexpected (expecting ";;")

```@Virtual Liberty: did u wanna know "i m using mint or other". I am using Ubuntu 9.10 (Karmic Koala)

---

### Post by Virtual Liberty on 2009-11-29
> **syeef said:**
> 
[/code]@Virtual Liberty: did u wanna know "i m using mint or other". I am using Ubuntu 9.10 (Karmic Koala)

No, I asked you why you can't install it from Ubuntu repositories because I was able to do so on Mint 8 without adding any additional software sources ( apparently they were already added ). Never mind .. my mistake :)

---

### Post by syeef on 2009-11-30
> **Virtual Liberty said:**
> Never mind .. my mistake :)
i didn't mind. tell me how is working ur opera in mint 8. did you satisfied with that?

---

### Post by Virtual Liberty on 2009-11-30
> **syeef said:**
> i didn't mind. tell me how is working ur opera in mint 8. did you satisfied with that?

Surprised me - instead of Firefox which ate ~100MB of RAM, it uses only ~20MB ( 6 tabs ). Pretty nice interface and of course, Speed Dial :)

---

### Post by mkvnmtr on 2009-11-30
There is an Opera repository that I enabled. Using it allows me to get updates. If you install from outside sources you will have to uninstall and reinstall every time you wish to update. Google it and you will find better instructions than I can give. It has been a while since I did it. The thing I miss is no-script in using Opera.

---

### Post by seenthelite on 2009-11-30
google opera, then go to the opera download page, the packages are available there.

---

### Post by kukibird1 on 2009-11-30
Here you go  [http://deb.opera.com/]("http://deb.opera.com/")

You can change lenny to stable.

---

### Post by Regenweald on 2009-11-30
Hey there op, better to download the deb here: [http://www.opera.com/download/?custom=yes](http://www.opera.com/download/?custom=yes)
and for alpha versions go here:
[http://snapshot.opera.com/unix/snapshot-4744/](http://snapshot.opera.com/unix/snapshot-4744/)

---

### Post by Orion8 on 2009-11-30
Why not search Synaptic (System -> Administration -> Synaptic Package Manager)?  It worked fine for me.   In the past I've downloaded a *.deb or *.rpm from Opera.com ([http://www.opera.com/browser/download/](http://www.opera.com/browser/download/)).  Double clicking installs things just fine.

---

### Post by syeef on 2009-12-08
> **kukibird1 said:**
> Here you go  [http://deb.opera.com/](http://deb.opera.com/)
You can change lenny to stable.
I go to the address and update the software source. then i install opera via terminal
```
sudo apt-get install opera
```I think this is the best way to install opera. but i m wrong, opera is added on my Applications>Internet menu but doesn't open when i click on that.

@[Orion8]("http://ubuntuforums.org/member.php?u=727403"): i did as u told. but opera doesn't run.

Thanks every body for try to help me. :D 

Is there any other way to install opera ?

---

### Post by oldsoundguy on 2009-12-08
Install this:

[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

Along with a nice package of utilities, it adds a gang of third party (but reliable) repositories to your sources list.
Then update.
(sudo apt-get update)
Then you can install Opera from Synaptic.

---

