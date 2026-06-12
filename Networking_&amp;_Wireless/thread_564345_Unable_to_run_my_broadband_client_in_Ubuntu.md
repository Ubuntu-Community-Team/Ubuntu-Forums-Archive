---
title: "Unable to run my broadband client in Ubuntu"
date: 2007-10-01
forum: Networking &amp; Wireless
---

### Post by amitabhishek on 2007-10-01
Hi,

I am a Sify broadband customer and use a Ubuntu Distro. Things went bad when I switched from Suse Linux to Ubuntu. After installation I cannot run the broadband client. I get this response whenever I try to connect:


amit@amit-desktop:~/Desktop$ cd sify_bbclient-3.0
amit@amit-desktop:~/Desktop/sify_bbclient-3.0$ sudo ./install.sh
Password:
Sify Broadband Client Installed Successfully
amit@amit-desktop:~/Desktop/sify_bbclient-3.0$ sifyconnect
sifyconnect: error while loading shared libraries: libssl.so.4: cannot open shared object file: No such file or directory
amit@amit-desktop:~/Desktop/sify_bbclient-3.0$



Post this I successfully installed openssl-0.9.8e but the error remain unchanged.My service provider also wanted gtk+-2.11.0 as a prerequisite which I tried installing and I got this response:



amit@amit-desktop:~/Desktop/Apps/gtk+-2.11.0$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking for native Win32... no
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.
amit@amit-desktop:~/Desktop/Apps/gtk+-2.11.0$


Can anyone please please please help.

Thanks in advance.

---

### Post by aashay on 2007-10-01
I used to use Antidialer to login to sify. Just grab the .deb from the foll link:
[https://sourceforge.net/project/showfiles.php?group_id=157014&package_id=175411]("https://sourceforge.net/project/showfiles.php?group_id=157014&package_id=175411")
Also call sify at the custcare and tell them to enable the linux version of the dialer for you.

---

### Post by amitabhishek on 2007-10-02
I did, when I tried to run anti-dialer this is the response I got:


amit@amit-desktop:~/Desktop$ sudo dpkg -i antidialer_0.2-1_i386.deb 
Password: 
Selecting previously deselected package antidialer. 
(Reading database ... 88002 files and directories currently installed.) 
Unpacking antidialer (from antidialer_0.2-1_i386.deb) ... 
dpkg: dependency problems prevent configuration of antidialer: 
 antidialer depends on libmcrypt4; however: 
  Package libmcrypt4 is not installed. 
 antidialer depends on libqt3-mt (>= 3:3.3.6); however: 
  Package libqt3-mt is not installed. 
 antidialer depends on libmcrypt4; however: 
  Package libmcrypt4 is not installed. 
 antidialer depends on libqt3-mt; however: 
  Package libqt3-mt is not installed. 
dpkg: error processing antidialer (--install): 
 dependency problems - leaving unconfigured 
Errors were encountered while processing: 
 antidialer 
amit@amit-desktop:~/Desktop$  



Kindly help.

---

### Post by wallgod on 2007-10-02
Hi
I have the same problem as you have. Calling Sify is quite cumbersome and some of the people who answer your call are quite naive about Linux (so am I). Anyway, this problem has not yet solved for me but I am told that it will get solved in the next 4 hours. 

The solution that they are going to apply is to bypass my IP so that I can connect to the internet. I have no idea what that means, but if it works then maybe you could ask them to bypass your IP too.

I will reply back here of the outcome of  'Operation IP Bypass' though I have serious doubts if it will really be done in the next 4 hours.

Good Luck!
:)

---

### Post by amitabhishek on 2007-10-02
Hi,

Thanks! Even I had horrid time with them sometime in the past.Kindly let me know if something comes out, frankly I feel for a company like Sify,  should have give us multiple BB clients for Linux.

Regards,
Amit

---

### Post by wallgod on 2007-10-02
Hi amit
The sify engineer was here for about 45 minutes sitting and reading the newspaper as his visit was only customary. He made some calls to some tech guy in SIfy who is supposedly going to bypass the IP address. After sitting for 45 minutes (and finishing the newspaper(mostly page3)) the engineer stretched out a bit and got up to call it a day. He announced with somewhat apathy that he will leave now and the bypass might take another hour or so.

There are only 2 things to be done now:
1. To keep the faith and let humanity dawn on Sify techies to help us in the next few hours.
2.To wonder if this problem is because of Fiesty Fawn(Ubuntu 7.04) and consider downgrading to the earlier version(6.06) because the engineer declared before leaving that even this cud be the reason for the error.

Not much of a choice there.

Anyway, What version are using? If you are using 6.06 and facing the same problem then the second option I presented above has no much meaning. So we are just left with what most Indians are left with in most situations: Faith!

---

### Post by amitabhishek on 2007-10-02
Hi,


Your response sure made a good reading. I will ensure to keep all the news papers away if Sify guys turn up:). Are you from Bangalore?

 Anyways am too using 7.04. I migrated from Suse to Ubuntu. In Suse I never had a problem like this ( but Suse 6.10 had problems in identifying my display and I used to get low resolution).For sometime I never used any of the MS products and it felt great, until now.

I have posted my  problem on few other Linux sites too, you can check them too :

[http://www.linuxquestions.org/questions/showthread.php?t=588537](http://www.linuxquestions.org/questions/showthread.php?t=588537)

Will keep you updated if I come across through a solution.

Rgds,
Amit

---

### Post by amitabhishek on 2007-10-02
Its working for me!:) You need to link your existing libssl & libcrypto files to the one being demanded by the dialer. Solution is at :

[http://www.linuxquestions.org/questions/showthread.php?p=2910493#post2910493](http://www.linuxquestions.org/questions/showthread.php?p=2910493#post2910493)

Pls Confirm once its working. you don't need Sify engineers now.

Rgds,
Amit

---

### Post by aashay on 2007-10-02
Believe me, antidialer is much better than the crap sify provides you.
Install the dependencies first:
```
sudo apt-get install libmcrypt4 libqt3-mt 
```
Then install antidialer using the .deb
Also if you have windows, you can boot into windows and login using the BBclient. Now ctrl+alt+del and kill the BBClient process. This leaves you logged into the service. When you boot into Ubuntu, your internet should be working

---

### Post by amitabhishek on 2007-10-02
Thanks that will be my plan B!:)

---

### Post by wallgod on 2007-10-03
Hi Amit
I m so happy that the solution of creating that symbolic link worked for u. Unfortunately for me it did not work. I dont know if I made any mistake. All i had to do was grab that text from the 'code' in the ugly solution and paste it in the terminal as root user, isnt it?

I did that and typed sifyconnect.. yet the same dreaded error!

Did it work for u because u had already done some things before like installing that ssl thing which u mentioned in your earlier posts? I downloaded some .rpm file for the same which ubuntu's archive manager fails to recognize.

Anyway, I m from Mumbai, my brother lives in Bangalore though.

Today the Sify guy who is **sitting **on my problem has called in sick. :mad:

:mad::mad::mad:

---

### Post by amitabhishek on 2007-10-03
Hi,

Don't worry, don't cut & paste, go to /usr/lib directory & search for your libssl & libcrypto files. It should be there because we are using the same distro.(7.04).

Now use ln command in the following way:

sudo ln -s/usr/lib/ <<your libssl &  libcrypto file>> /usr/lib/libssl.so.4 

once done, verify it by right clicking the your (just created) libssl.so.4 file it should link to the respective files already in your /usr/lib directory.

Best of luck & keep me posted.

Regards,
Amit Abhishek

---

### Post by wallgod on 2007-10-04
Hi Amit
I tried doing what you said but discovered that there is no file called libssl.so and the icons for libssl.so.4 and libssl.s have a small red cross on them. These are both links to libssl.so which is missing!

WOuld it be possible to rectify this error by simply procurring the libssl.so file from elsewhere and pasting it in usr/lib/?

do u know some place i can get it from?

Many thanks in advance

---

### Post by wallgod on 2007-10-06
Hi Amit
My problem is solved! No i did not uninstall Ubuntu and go back to Windows! The Sify guys bypassed my IP and now I login straight from a webpage. No dialer required!

Thanks for the support anyways! If ever you are in Mumbai and have a problem finding place to live, you can come to the J W Marriot hotel. I own it! I mean at the moment I m very happy and I feel like I own everything, what the hell is J W Marriot?

:guitar:

---

