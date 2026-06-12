---
title: "Modem"
date: 2006-09-17
forum: Networking &amp; Wireless
---

### Post by mitchmaster on 2006-09-17
Hey... My name is Mitch and I have been trying for a long time to get my 'winmodem' to work.
I have run scanmodem, and have tried my hardest to follow the directions. The problem is, I am not super smart and need someone who can explain these steps in plain english 'exactly' as a person would have to enter it in pretty much...

Here are all the files that Scanmodem gave me:
[http://h1.ripway.com/mitch41/Linux/index.html]("http://h1.ripway.com/mitch41/Linux/index.html")

That link provides links to all of the files that you should need.

Thanks in advance!

Mitchhhhh

---

### Post by sprucas on 2006-09-17
have you done the following as suggested in the output of modemdata.txt??

The modem lacks a Subsystem

Get the package  SLMODEMD.gcc4.tar.gz from [http://linmodems.technion.ac.il/packages/smartlink/](http://linmodems.technion.ac.il/packages/smartlink/)
Open a termial and unpack under Linux with:
$ tar zxf  SLMODEMD.gcc4.tar.gz .
and read the Quick Instructions at the beginning of file 1st_Read.txt in new folder  SLMODEMD.gcc4/ .
Briefly, the following two Root commands should set up the modem:
    sudo modprobe snd-hda-intel
    sudo slmodemd --alsa -c YOUR_COUNTRY hw:0,1
which should create ports:
    /dev/ttySL0 -->  /dev/pts/N  , with N some number
Find YOUR_COUNTRY from the listing displayed by:
    sudo slmodemd --countrylist

---

### Post by sprucas on 2006-09-17
also try [https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)

---

### Post by mitchmaster on 2006-09-17
I have done my best to follow those instructions you posted for that... and i have the SLMODEM thing and everything but its the modprobe part that i get stuck on... thats why i was hoping someone could clarify the instructions or explain them so they make sense for me...

---

### Post by hasala on 2008-02-06
(if you use this method you can forget about the rpms no rpm will be needed to be installed for you to get the modem running.)
RATHER THAN EXTERNAL MODEMS internal modems offloads a lot of funtionality to the software driver.it has always been a big problem to configure those internal modems or(WINMODEMS/LINMODEMS) to work with linux because of manufacturers not supporting linux (and also the driver being pretty much more complex than ) But due to a great person Linux maintainer Sasha Khapyorsky writing the neccassary drivers needed to work the winmodem , now using a internal modem in linux has become as easy as ABC.


Linux maintainer: Sasha Khapyorsky. Get his updated software from:
[http://linmodems.technion.il/packages/smartlink/](http://linmodems.technion.il/packages/smartlink/)


what to do.

1. download a software called scanmodem from the foresaid site.

2. Browse [http://linmodems.technion.ac.il](http://linmodems.technion.ac.il) and  download scanModem.gz .
 Within a Linux partition open up a console and type in the following commands
    gunzip scanModem.gz
 To make it executable:
    chmod +x scanModem
 Run diagnositics with:
    ./scanModem 
3.scanmodem will check your hardware and software and then write its diagnostics to a subdir called modem.

4.open the ModemData.txt file.and go to   -----------end Softmodem section----------- part .

5.it will give the softwares you need to download and install.

6.if u have not installed the source at the installation of the distro. please install it.(source of the kernel) from the installation cd/dvd.

7.then install the downloaded software.

8.go to scanmodem/modem and open the diagnostic file chipsetname.txt eg:Smartlink.txt/conexant.txt .

9.In the start of the doc it gives the commands you have to run at the console to load the drivers that u downloaded and installed.

10.make sure that the smpppd, pppd services are installed and running.else install both and remember to enable them.

11.dial up using kinternet(i prefer it) or kppp. put to stupid mode option..now configure kinternet and the modem properly.to do that 
 goto yast->network devices ->modem.
           1.choose your modem device and press edit.
              enter modem device as /dev/ttySL0 and enter the details of the isp. if you are not sure call customer support for internet of your isp (internet provider) and get the required details such as number to dial and prefix.username
and password.

           2.remember to definitely check the box for stupid mode.

now every thing is set up

enjoy the internet with a great browser like firefox/opera.!!!!!!!
(with this you do not need any rpm for you to download,what you compile is enough)
if u have any comments or questions please mail to:dharmawardena_06@elect.mrt.ac.lk

						or [email]hasaladharmawardena@yahoo.com[/email]
or //(hasalaid@gmail.com).

hasala dharmawardena
faculty of engineering
department of electrical engineering([www.elect.mrt.ac.lk](www.elect.mrt.ac.lk))
University Of Moratuwa
SRILANKA

regards from srilanka , hasala.         ([www.hasala.bravehost.com](www.hasala.bravehost.com))

---

