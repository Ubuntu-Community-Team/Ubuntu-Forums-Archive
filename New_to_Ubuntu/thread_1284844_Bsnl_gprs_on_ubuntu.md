---
title: "Bsnl gprs on ubuntu"
date: 2009-10-07
forum: New to Ubuntu
---

### Post by parminder_mangat on 2009-10-07
Hello frnds i have nokia 6233 and i use gprs dial up. My access point name is bsnlnet and dialup no. is *99#. when i make a connection the connection establish but data transfer does not take place. every time it happens. but with same configuration internet works on MS windows. Anyone please help. I am using jaunty jackope 9.04 .

---

### Post by dineshs on 2009-10-07
can you ping 4.2.2.1

---

### Post by baskar007 on 2009-10-07
I am also using BSNL but not mobile, using NIC card.

to determine your problem : 

Post ping results.

check your secure methods  on connection settings

---

### Post by parminder_mangat on 2009-10-07
What is ping and how to use it?

---

### Post by dineshs on 2009-10-07
Open a terminal (applications-accessories - terminal)and type the following command after you connect to the internet.

ping 4.2.2.1

then  post the output
note:4.2.2.1 is the IP address of an open DNS server and we are checking whether there is reply

---

### Post by parminder_mangat on 2009-10-07
Ok i will check. wait for some time because there is electric cut now.

---

### Post by parminder_mangat on 2009-10-07
The comand is only ping 4.2.2.1 or 
sudo ping 4.2.21

---

### Post by dineshs on 2009-10-07
sudo is not required

---

### Post by parminder_mangat on 2009-10-07
64 bytes from 4.2.2.1: icmp_seq=66 ttl=42 time=632ms
the time was continuosly changing sometimes 539,400,666 etc. and the whole process was not ending so i closed the terminal.

---

### Post by dineshs on 2009-10-07
Now open firefox web browser and try this site (type this on the address bar)
64.233.189.104

---

### Post by parminder_mangat on 2009-10-07
It is opening google search page with some bar codes in place of google logo. when i place cursor over those bar codes it shows invention of bar codes

---

### Post by dineshs on 2009-10-07
If you are getting google when you type the said IP then I think it is a DNS issue .To solve this edit the file /etc/resolv.conf using the command

sudo gedit /etc/resolv.conf

A text file will open after you enter password.Add the following line at the end

nameserver 4.2.2.1

save and close the file .Now try a site

---

### Post by parminder_mangat on 2009-10-07
Thanx friend it is working now. Thank you very much.

---

### Post by t0p on 2009-10-07
post deleted

---

### Post by baskar007 on 2009-10-07
> **parminder_mangat said:**
> It is opening google search page with some bar codes in place of google logo. when i place cursor over those bar codes it shows invention of bar codes
today is the date invention of bar codes  Thats why google is displaying its logo like barcode :lol:

---

### Post by parminder_mangat on 2009-10-07
will it work now permanently or i have to repeat whole procedure every time?

---

### Post by parminder_mangat on 2009-10-07
Tell me one more thing, can i download KDE seperately to install it in ubuntu? is it a .deb file? if yes what is the link then.

---

### Post by baskar007 on 2009-10-07
> **parminder_mangat said:**
> will it work now permanently or i have to repeat whole procedure every time?
ya after reboot resolv.conf file will reset. you need to edit to again.

change DNS address using network connection manager.  then your DNs setting will never reseted.

---

### Post by baskar007 on 2009-10-07
> **parminder_mangat said:**
> Tell me one more thing, can i download KDE seperately to install it in ubuntu? is it a .deb file? if yes what is the link then.
open terminal and run this code

sudo apt-get install kubuntu-desktop

---

### Post by parminder_mangat on 2009-10-07
> **baskar007 said:**
> ya after reboot resolv.conf file will reset. you need to edit to again.

change DNS address using network connection manager.  then your DNs setting will never reseted.

change dns adress to which?

---

### Post by parminder_mangat on 2009-10-07
> **baskar007 said:**
> open terminal and run this code

sudo apt-get install kubuntu-desktop

actually i want a standalone offline installer of kde.

---

### Post by baskar007 on 2009-10-07
> **parminder_mangat said:**
> change dns adress to which?
first open network connections
and then goto your connection type, i thing its a mobilebroadband.
then double click on your connection name.
It will open a new window. in that window select IPv4 setting

select method to automatic(ppp0) addresses only

and then enter 192.168.41.163 in DNS servers. and click ok.

192.168.41.163 this is a DNS server address for BSNL

---

### Post by parminder_mangat on 2009-10-07
i am in punjab will the dns server be same?

---

### Post by baskar007 on 2009-10-07
> **parminder_mangat said:**
> actually i want a standalone offline installer of kde.

I have attached a list of link i used for downloading KDE for my Ubuntu before two days.

i think you will download kde in different computer. so its probably XP .
you need freeDownload manager to Download all files listed on this txt file.

go to fdm.org to download freedownload manager and install it on windows.

then goto file menu and select import txtfile for download.
now you have done. fdm will download all of these files automatically.

---

### Post by baskar007 on 2009-10-07
> **parminder_mangat said:**
> i am in punjab will the dns server be same?
i thing this dns will work. because this server is located on Delhi.

---

### Post by parminder_mangat on 2009-10-07
> **baskar007 said:**
> I have attached a list of link i used for downloading KDE for my Ubuntu before two days.

i think you will download kde in different computer. so its probably XP .
you need freeDownload manager to Download all files listed on this txt file.

go to fdm.org to download freedownload manager and install it on windows.

then goto file menu and select import txtfile for download.
now you have done. fdm will download all of these files automatically.

thanx. but is it a .deb file? if not then how to install it.

---

### Post by parminder_mangat on 2009-10-07
Do you use bsnl too? what is rent there for unlimited monthly gprs. Actually i sit on pc rarely so i will download kde on my mobile and then transfer it to pc. I am on mobile now. what is the size of kde?

---

### Post by parminder_mangat on 2009-10-07
@bhaskar ur blog is interesting i am suscribed to rss feeds.

---

### Post by baskar007 on 2009-10-07
> **parminder_mangat said:**
> thanx. but is it a .deb file? if not then how to install it.
all are deb files. and use install all of 247 files by one command " sudo dpkg -i *.deb"

if you need detailed help. visit this link.

[http://softwareroxer.blogspot.com/2009/10/howto-backup-and-restoring-debpackages.html](http://softwareroxer.blogspot.com/2009/10/howto-backup-and-restoring-debpackages.html)

in this link read  **Re-Installing of Backup: **you will get a idea to how to install.

---

### Post by baskar007 on 2009-10-07
> **parminder_mangat said:**
> Do you use bsnl too? what is rent there for unlimited monthly gprs. Actually i sit on pc rarely so i will download kde on my mobile and then transfer it to pc. I am on mobile now. what is the size of kde?
ya i am using BSNL NIC. Its really really slooooooooow.
Still i am using this because i have no income to get broadband or other . (i am studying)

then rent is 276 RS/month. 
speed it 30kBps.

---

### Post by baskar007 on 2009-10-07
> **parminder_mangat said:**
> @bhaskar ur blog is interesting i am suscribed to rss feeds.
thank you. thank you very much. :lol:

---

### Post by parminder_mangat on 2009-10-07
i m a student too, of mechanical engineering. in punjab bsnl provide gprs card for Rs 193 with one month validity and Rs 10 talktime.

---

### Post by parminder_mangat on 2009-10-07
what is size of kde, i mean how much MB or GB?

---

### Post by parminder_mangat on 2009-10-07
I have installed ubuntu in windows xp but it on separate drive. (xp is on C and ubuntu is on D) will my ubuntu work when i delete xp?

---

### Post by baskar007 on 2009-10-07
> **parminder_mangat said:**
> i m a student too, of mechanical engineering. in punjab bsnl provide gprs card for Rs 193 with one month validity and Rs 10 talktime.
I hate BSNL because of many reasons.
last time my modem firmware was corrupted so  went to customer care and i asked for repair or reinstalling.   the BSNL service engineer said they have no firmware for this. i asked for replacing , he said no stock. even i have warrenty for 6months to NIC 
their customer care is worst.
firmware corruption is a small problem one flash can solve this problem.
after contacting customer care of bsnl. I did myself flashing my modem with Vodafone flash file.

[parminder_mangat]("http://ubuntuforums.org/member.php?u=873214") If you have a idea to get BSNL net then change your opennion.

---

### Post by baskar007 on 2009-10-07
> **parminder_mangat said:**
> I have installed ubuntu in windows xp but it on separate drive. (xp is on C and ubuntu is on D) will my ubuntu work when i delete xp?
yes sure. but your grub loader will not work.
solution is : [http://softwareroxer.blogspot.com/2009/09/grub-cannot-detect-windows-vista-after.html](http://softwareroxer.blogspot.com/2009/09/grub-cannot-detect-windows-vista-after.html)

note: don't think i am always diverting you to my blog. because i am too lazy to write full details on this page

---

### Post by parminder_mangat on 2009-10-07
i already have one and it works fine. what is size of kde?

---

### Post by baskar007 on 2009-10-07
> **parminder_mangat said:**
> i already have one and it works fine. what is size of kde?
i think 142Mb total for all files.

---

### Post by dineshs on 2009-10-07
> **baskar007 said:**
> i thing this dns will work. because this server is located on Delhi.

This is a private IP ,So better ask BSNL to confirm.Anyway you can use 4.2.2.1.

---

### Post by parminder_mangat on 2009-10-07
> **dineshs said:**
> This is a private IP ,So better ask BSNL to confirm.Anyway you can use 4.2.2.1.

but i have to setup everytime with 4.2.2.1 i want a permanent fix. is dns server my ip address?

---

### Post by baskar007 on 2009-10-07
> **parminder_mangat said:**
> but i have to setup everytime with 4.2.2.1 i want a permanent fix. is dns server my ip address?
[http://ubuntuforums.org/showpost.php?p=8066192&postcount=22](http://ubuntuforums.org/showpost.php?p=8066192&postcount=22)

---

### Post by parminder_mangat on 2009-10-08
> **baskar007 said:**
> [http://ubuntuforums.org/showpost.php?p=8066192&postcount=22](http://ubuntuforums.org/showpost.php?p=8066192&postcount=22)

but that dns server address does not solve the problem.

---

### Post by baskar007 on 2009-10-08
> **parminder_mangat said:**
> but that dns server address does not solve the problem.
Do you have IPv6 disabled on your system?
If no go here: [URL="http://ubuntuforums.org/showthread.php?t=1275491"]http://ubuntuforums.org/showthread.php?t=1275491
[/URL]

---

### Post by parminder_mangat on 2009-10-09
I wrote dns server address 4.2.2.1 and now the issue is solved. I think this thread will help other bsnl users too.

---

