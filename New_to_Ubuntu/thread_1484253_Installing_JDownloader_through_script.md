---
title: "Installing JDownloader through script"
date: 2010-05-15
forum: New to Ubuntu
---

### Post by webwiller on 2010-05-15
1.
      wget must be installed on system!
   2.
      Download jd.sh
   3.
      chmod +x jd.sh
   4.
      start jd.sh

I'm trying to install JDownloader and I have to follow the above instructions. I get away with downloading the script on my desktop, but when I open terminale and do:
```
chmod +x jd.sh
```

I get: no such file or directory.

What am I doing wrong?

thx in adv! ;)

---

### Post by Ozymandias_117 on 2010-05-15
Are you in the right Directory? GNU/Linux is case-sensitive, are you sure the program is jd.sh not Jd.sh or JD.sh?

---

### Post by Keith1212 on 2010-05-15
This is the guide I used. I forget who wrote it so credit goes to them.

What your trying to do is make the jd.sh and executable file. U need to make sure jd.sh is in your Home folder. Then cd to that folder in your terminal and execute the command. Or browse there in the file manager and right click properties of jd.sh and check the box to make it executable.
> For those who still bump their head in JD in Ubuntu do this


sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-jdk sun-java6-plugin
(TAB button to be able to click OK)
sudo update-java-alternatives -s java-6-sun


wget -c [http://212.117.163.148/jd.sh](http://212.117.163.148/jd.sh)
chmod +x jd.sh
./jd.sh


after install
make a short cut in your panel rightclick -> add to panel-> make a shortcut->add-> Type: Program in Termilnal Name: "JD", CMD: "sudo ./jd.sh" , Coments:what ever u like. -> and OK

next time hit this shortcut and enter your root pass


---

### Post by Troublegum on 2010-05-15
You can install Jdownloader through synaptic. There's a PPA on Launchpad.
```

sudo apt-add-repository ppa:jd-team/jdownloader
sudo apt-get update
sudo apt-get install jdownloader

```

---

### Post by SurajSingh on 2010-06-01
its the best method as far as online installation is concerned ....what if someone has to install jdownloader in an  offline method .....i guess whatever installations instructions offered in any threads for installation of any application should be discussed in online and offline manner both if possible....and if its either too difficult or not possible to install in offline way then the reason should be told. i dont kno whether jdownloader can be installed in offline way so tell me :P plz.

---

### Post by mac9416 on 2010-06-01
SurajSingh, you can install jdownloader offline using [Keryx]("http://keryxproject.org"). Simply create your project and add this line to the sources list: deb [http://ppa.launchpad.net/jd-team/jdownloader/ubuntu](http://ppa.launchpad.net/jd-team/jdownloader/ubuntu) karmic main

---

### Post by SurajSingh on 2010-06-03
thanks :D hurrraay :P

---

### Post by oktapod on 2010-07-06
Thanks Troublegum.

---

### Post by TimEnid on 2010-07-13
> **Troublegum said:**
> You can install Jdownloader through synaptic. There's a PPA on Launchpad.
```

sudo apt-add-repository ppa:jd-team/jdownloader
sudo apt-get update
sudo apt-get install jdownloader

```


new to ubuntu. how can i install jdownloader using this method?

---

### Post by mac9416 on 2010-07-13
Hi, TimEnid,

That method should work for you. All you have to do is open a terminal (Applications > Accessories > Terminal), and then copy those commands into it. When you enter the first command and hit <enter>, you'll be asked for your password. As you enter the password, you won't see it being entered, but it is. After the third command, JDownloader will be installed.

---

### Post by TimEnid on 2010-07-14
> **mac9416 said:**
> Hi, TimEnid,

That method should work for you. All you have to do is open a terminal (Applications > Accessories > Terminal), and then copy those commands into it. When you enter the first command and hit <enter>, you'll be asked for your password. As you enter the password, you won't see it being entered, but it is. After the third command, JDownloader will be installed.
it worked, thanks,  but, when i went to open jdownloader, it installed the update and hung at 99%. i let it sit for about 30 minutes thinking something would happen, but nothing. Any suggestions.

---

### Post by mac9416 on 2010-07-14
If JDownloader installed correctly, and you're now having trouble getting it to start, you should open up a new thread for that. You should also ask on [their forum]("http://board.jdownloader.org/") since you'll be more likely to get good help there.

---

### Post by EXCiD3 on 2010-07-14
> **TimEnid said:**
> it worked, thanks,  but, when i went to open jdownloader, it installed the update and hung at 99%. i let it sit for about 30 minutes thinking something would happen, but nothing. Any suggestions.

Just try for closing JDownloader and try it again. I've had that issue happen to me before as well.

---

### Post by raman1478 on 2010-12-16
how do i create launcher for JDownloader

Thanks

i already did these

sudo add-apt-repository ppa:jd-team/jdownloader
sudo apt-get update
sudo apt-get install jdownloader

---

