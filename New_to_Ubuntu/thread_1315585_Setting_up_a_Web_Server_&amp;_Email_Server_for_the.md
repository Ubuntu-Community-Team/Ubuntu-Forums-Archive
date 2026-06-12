---
title: "Setting up a Web Server &amp; Email Server for the first time..."
date: 2009-11-05
forum: New to Ubuntu
---

### Post by Bradyhawke on 2009-11-05
Hello Ubuntu users!

New member here, and I'm planning on setting up both a Web Server & an Email Server using Ubuntu for the first time.  I've built plenty of computers over the years, and have relied on Microsoft for all my operating system needs.  Now, because of my interests in web design, I'm looking into setting up a web server and email server for me and some of my friends and relatives to use while we work on various pet projects and help each other out.  I'm doing this more for myself as a hobby and to learn about Ubuntu, so it's not like I have people relying on me to get it "up and running" in a week.

I've spent quite a bit of time reading throught the forums to get a better understanding of Ubuntu, as well as picking up this book from Barnes & Noble ([http://search.barnesandnoble.com/Official-Ubuntu-Server-Book/Kyle-Rankin/e/9780137036035/?itm=1&usri=Ubuntu+server+book](http://search.barnesandnoble.com/Official-Ubuntu-Server-Book/Kyle-Rankin/e/9780137036035/?itm=1&usri=Ubuntu+server+book))

I have plenty of spare computers, parts and new parts that I can use to start out with, which is why I decided to build two separate servers instead of loading all services into one server.  Also, I have five static IP addresses available to use here at home, so any of these servers will be placed on their own static IP address.

Here's a brief rundown of what I have hardware-wise and the plan for deployment - and I'd thought it would be wise to detail the plans and parts just in case someone notices something that may be a problem for me later on.

**Web Server:**

[LIST]
[*]Intel D865PERL P4 motherboard
[*]Intel P4 2.8Ghz Hyper Threading CPU
[*]2GB DDR400 memory (4 x 512MB sticks)
[*]WD 320GB SATA HDD's x (2)
[*]Addonics SATA II PCI-X RAID5/JBOD 4-port controller
[*]D-LINK DGE-530T 10/100/1000 PCI network adapter
[*]Sony Optiarc CD-RW IDE drive
[*]Mid-Tower case with a 600-watt power supply
[/LIST]
* Planning on a new, clean installation of Ubuntu Server 9.04 (32-bit) with LAMP.
* Planning on using the two 320GB HDDs in a RAID 1 configuration.
* Eventually will be adding two more HDDs - 320GBs or larger - as needed.
* This Web server will have its own static IP address.


**EMAIL Server:**

[LIST]
[*]ASUS P4P800SE P4 motherboard (Gigabit LAN & SATA x 2 onboard)
[*]Intel P4 3.0Ghz Hyper Threading CPU
[*]2GB DDR400 memory (4 x 512MB sticks)
[*]WD 320GB SATA HDD's x (2)
[*]Addonics SATA II PCI-X RAID5/JBOD 4-port controller
[*]Sony Optiarc CD-RW IDE drive
[*]Mid-Tower case with a 600-watt power supply
[/LIST]
* Planning on a new, clean installation of Ubuntu Server 9.04 (32-bit).
* Planning on using the two 320GB HDDs in a RAID 1 configuration.
* Eventually will be adding two more HDDs - 320GBs or larger - as needed.
* This Email server will have its own static IP address.


Server Questions -[INDENT]
[LIST=1]
[*]Can I run a DNS server & Web server on the same workstation? (might be a really simple question, and it looks like from what I have read so far that I can, but I thought I'd just ask for verification) - And do I even need to run my own DNS server in the first place?
[*]I have a 3 year old Sony Laptop (works fine but has a damaged screen) available to use - so if need be, should I set that up as a DNS server on its own static IP address?
[*]Should I install Ubuntu WITHIN the RAID 1 array or on a separate HDD and set up the RAID 1 array for data only? (I'm a bit confused by all the different options I've read up on here in the forums) - And if I set up Ubuntu on a separate HDD, do I need to set THAT drive up in another RAID array to protect it from data loss?
[*]If I was planning on sharing the Web server with 2-3 other people (sister in Florida, cousin in California...), what [COLOR=RoyalBlue]**FREE Control Panel**[/COLOR] would be best for me to install? (Webmin?)
[*]When I add HDDs at a later date, would it be wise to continue with the RAID 1 array configuration, or should I consider porting to a different array?  Or should I take the time out now and set up a bigger array so as to avoid the porting process?  I have six 320GB HDDs available atm, so should I consider using four HDDs in a RAID 5 or RAID 10 array?
[*]For the Email server, I was planning on going with a IMAP server configuration - but really, I need to spend much more time researching what my options for setting this up are.  So what I would like to know is (other than the forums) what source of information (book, web, etc.) is there out there that can provide more detailed information / instruction for setting up an Email server using IMAP than the book I listed above?
[/LIST]
[/INDENT]Sorry if this is a bit long, but I just like providing as much info as I can offer up in the first place.  Please feel free to point out any plan/design flaws I may have listed - and provide any help you can.

Thanks to all in advanced, time for me to go to work!

---

### Post by Hilgo on 2009-11-05
I'll try to answer some of your questions

1) Yes, you can run DNS and web server on the same system. In your case i would even recommend it since it doesn't look like you'll serve a lot of people. In my humble opinion a separate DNS server would be overkill.

2) Nope, won't be necessary.

3) I would put it all in 1 big raid array since the server won't be hammered. If i was configurating the server for work i'd make 1 raid 1 array for the OS and a second, raid 5, array for the data. But their are, of course, a lot of different ways in this case which all work perfectly well.

4) Webmin would be my choice and a lot of time & effort in making sure the firewall is configured correctly since sharing it would mean connecting it to the internet where all the evil hackers are ;) Thinking about it I probably use the laptop as a separate firewall (I'm a big smoothwall fan) and forward the webmin port (and other ports if needed) to the server(s).

5) Depends on what you use in the 1st place. I think I'd add them to the current raid set up instead of a separate one.

6) Can't help you with this one because I have no experience with email servers on linux (yet).

Good luck with your project, it looks like it could be a lot of fun getting it all to work :)

---

### Post by Bradyhawke on 2009-11-06
Thanks for the reply Hilgo!

Spent some time last night looking into SmoothWall and Webmin, but I think I'll start my Web server build today and see how it goes.  I do like the idea of setting up the laptop (with the broken screen) as a firewall...

---

### Post by Bradyhawke on 2009-11-08
OK, I've completed my first install of Ubuntu 9.04 Server edition (32-bit) on the Web server box I've built (see stats in OP), but instead of 2 HDD's I went with 4 HDD's.

After an initial mistake (I configured the RAID array in the BIOS and Ubuntu only saw it as 2 HDD's instead of 4), I started the install over again from scratch (I went back into the BIOS and deleted the RAID configurations I previously made) and made it all the way back to the point of the installation where I need to partition the disks.  Here is what the HDD details/info screen says:

SCSI5  (0,0,0)  (sda)  - 320.1 GB ATA WDC WD3200AAJS-0
SCSI6  (0,0,0)  (sdb)  - 320.1 GB ATA WDC WD3200AAJS-0
SCSI7  (0,0,0)  (sdc)  - 320.1 GB ATA WDC WD3200AAJS-0
          #1   primary  292.3 GB           ext3
         #5   logical        3.1 GB     F    swap                  swap
                pri/log      24.7 GB           FREE SWAP
SCSI8  (0,0,0)  (sdd)  - 320.1 GB ATA WDC WD3200AAJS-0
         #1   primary  292.3 GB           ext3
         #5   logical        3.1 GB     F    swap                  swap
                pri/log      24.7 GB           FREE SWAP

Now, I understand that the partitions of SCSI7 & SCSI8 are from the previous installation, and I'm not even concerned about saving them (plan is to format those), so please ignore them.  But I do have a serious question about WHAT type of partition setup I should go with - Really, I'm looking for a recommendation as to what partition format to make.  I'm completely new to this, so I do need help setting up a partition scheme.

The plan for this server is to use it as a Web server for me and several other people that will access it from the internet.  I am planning on using WEBMIN to set up various accounts for each of us to use.  This Web server will have it's own static IP address.  I'm also curious about which RAID array would be best to use. I'm leaning towards using RAID 1 (I really like having the fault tolerance), but I was curious if I should consider using RAID 5 or RAID 10 (after reading more about RAID 10, I'm starting to lean in that direction).

So, here's my new list of questions:

1) What partition scheme would be good for a Web server with no more than 10 accounts (users who access it) on it?

2) Should I be making a separate partition for each and every user (account) that will be administered thru WEBMIN or is that something that will be controlled via the WEBMIN installation/program?  Would it be considered a good idea to create these separate partitions now BEFORE installing WEBMIN for added security or in case I choose to use a different Control Panel?

3) Will the RAID array I choose to use determine which partition scheme would work best, or does it not matter about what partitions i set up for any type of RAID array?

4) I was planning on using a RAID 1 array with just two 320GB HDDs, but since I've moved to four 320GB HDDs, should I stick with the RAID 1, or move to RAID 5?  Should I consider setting up a RAID 10 array?

Anyone who has set up a RAID 10 array using Ubuntu server 9.04 (32-bit) - I'd love your input on any issues you may have had.  And just a quick thank you to everyone who can help out with any of these question...

---

### Post by CharlesA on 2009-11-08
With 4 drives you can run either RAID-5 or RAID-10. If you want to run with RAID-1, you'd only use 2 disks in 2 separate arrays.

---

