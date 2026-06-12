---
title: "OpenOffice 3.0 and now 3.1 do not work"
date: 2009-06-13
forum: New to Ubuntu
---

### Post by giancast on 2009-06-13
Today I started with not being able to open OpenOffice 3.0. The OpenOffice splash screen came up and it gave me the error "Cannot determine the language" and then it closed. So I decided to upgrade to 3.1 and followed the instructions in another website. It installed. I can see it in Synaptic Package Manager, all the OpenOffice lines were 3.0 and now say 3.1.0. I rebooted and now I do not get the language message, all I see is the OpenOffice splash screen and then it goes away and nothing happens. 

I am running 9.04 64Bit. The OpenOffice that was installed I think it was the 64Bit since it was on the iso CD.

Any help would be appreciated. 

Thanks.

---

### Post by synapsys on 2009-06-13
Un-install and re-install

---

### Post by sandyd on 2009-06-13
maybe....

```

cd ~
rm -rf .openoffice.org

```

and try running it in terminal
```

openoffice.org3 -writer %U     

```
see if you can catch the error there

---

### Post by esalnoj on 2009-06-13
Did you remove openoffice 2.4 with synaptic first?
That hung me up when I was installing 3.1.

The following install code worked for me on both intrepid and jaunty:

[Assuming tar file on Desktop]
```
cd Desktop
tar xzvf OOo_3.1.0_LinuxIntel_install_en-US_deb.tar.gz
cd OOO310_m11_native_packed-4_en-US.9399/DEBS
sudo dpkg -i *.deb --install
cd desktop-integration
sudo dpkg -i openoffice.org3.1-debian-menus_3.1-9393_all.deb
```

This should be the exact code you need, but may need the file names and directories changed.

---

### Post by giancast on 2009-06-14
To ESALNOJ :
I had OO 3.0 so I went to Synaptic and marked for complete removal all the OO packages. So yes I did unistalled the previous version. I will try your terminal installation and see what happens.
To CARLEE:
I ran the openoffice.org3 - writer %U and only got:
giancarlo64@giancarlo64-desktop:~$ openoffice.org3 -writer %U
bash: openoffice.org3: command not found
 Any ideas?

---

### Post by fooman on 2009-06-14
have a look at this guide:

[http://ubuntuforums.org/showthread.php?t=987181](http://ubuntuforums.org/showthread.php?t=987181)

if you have already uninstalled OO....just add the appropriate repos as in the guide,  then run these commands (one at a time) in a terminal:

```
sudo apt-get update && sudo apt-get upgrade 
sudo apt-get install openoffice.org
```hope that helps.

---

### Post by giancast on 2009-07-08
I actually fixed the problem. It looks like when the upgrade was done the permissions got changed to root only. So I changed the permissions to allow user to be able to read, write and delete. After I did that OO3.1 worked.

Why would the permissions change is beyond me, but at least is working. Thanks to all that replied.

---

