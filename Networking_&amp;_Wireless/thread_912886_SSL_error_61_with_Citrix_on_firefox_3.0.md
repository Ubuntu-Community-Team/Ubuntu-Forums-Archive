---
title: "SSL error 61 with Citrix on firefox 3.0"
date: 2008-09-07
forum: Networking &amp; Wireless
---

### Post by Pascou22 on 2008-09-07
Hello every one!

      I work on this issu yesterday and i want to give the fix if anyone else is experiancing the same issue. 


      It is cause by missing certificat on linux Ica Client. The solution is : "cp /usr/share/ca-certificates/mozilla/* /usr/lib/ICAClient/keystore/cacerts/"

      In other word's copy your mozzilla firefox certificat to the citrix instalation folder.

      Hope this will help you!

---

### Post by Bogak on 2008-09-29
Thank you Pascou22!

Now I can work from home, and no longer have a reason to dual boot!

Bogak

---

### Post by Pomo on 2008-09-30
This should be a sticky. I have been searhing for ages to find a way to work in citrix on Ubuntu.
Finally this solved my problems...

---

### Post by blnl on 2008-10-05
Thank you Pascou22!

After days of searching the web I was about to give up.
Although I'm using opensuse this worked for me as well.

I hope you don't mind if I post this solution at the suse forum.

---

### Post by VanguardOutlander on 2008-11-09
I wrote a mini howto to fix this citrix ssl 61 error:
[http://geekpete.com/blog/tech-guides/linux-citrix-client-error-61-ubuntu-810-intrepid-ibex](http://geekpete.com/blog/tech-guides/linux-citrix-client-error-61-ubuntu-810-intrepid-ibex)

---

### Post by bozovilla on 2009-03-25
Hi, I am unable to paste the file into /usr/lib/ICAClient/keystore/cacerts. A message says permission denied. How can I resolve this? Thanks

---

### Post by SnackMasterX on 2009-05-08
I am having this problem and tried everything. I know I have the correct .crt file because it works just fine under windows regardless of whether I use IE or firefox but for some reason even though I have made sure the .crt file is under /use/lib/ICAClient/keystore/cacerts I am still getting SSL error 61. Does anyone have any suggestions?

---

### Post by Jam3s0n on 2009-05-21
I worked on this problem for a couple days. There is lots of words out there, but very few that helped me. I did get it to work by compliling various methods. I will list them here; mostly all methods are biased towards using Mozilla (or so it seems). I would install [Seamonkey]("http://www.seamonkey-project.org/") before you even start these steps, just in case Mozilla doesnt work.

1. Goto this thread [http://ubuntuforums.org/showthread.php?t=1105855](http://ubuntuforums.org/showthread.php?t=1105855) and do what it says in the first post.

2. There is lots of people that will tell you to copy and download certificate files. Using the following command, you shouldn't need to do any of that (as long as you have Mozilla already installed):

  sudo cp /usr/share/ca-certificates/mozilla/* /usr/lib/ICAClient/keystore/cacerts/

3. If it is still not working under Mozilla, download [Seamonkey]("http://www.seamonkey-project.org/") and try it with Seamonkey.
  Note: you may need to reinstall Citrix, but beyond that nothing else.

I do not understand as to why I couldn't get Citrix to work under Mozilla and was getting very frustrated because I searched and implemented the methods that everyone else said worked. The only thing that seemed to fix my problems was having Seamonkey already installed. In a desperate attempt, I decided to give it a try and it worked. Good luck.

---

### Post by pablitoneal on 2009-07-24
thanks so much pascou.  i copied your command into the terminal and my citrix worked immediately.  you are a godsend!

---

### Post by rifd on 2009-12-15
Thank you, worked for me. Just begin with sudo if you have permission errors

---

### Post by lordoja on 2010-01-12
i have the same error, however mine says that i have not chosen to accept the cert, i dont see an option anywhere to do this, HELP!

---

### Post by MrChainBlueLightnin on 2010-02-13
Thanks rifd!  Sudo did it!  Ova, just do what the thread says.

---

### Post by MrChainBlueLightnin on 2010-02-13
I love hearing about people like Bogak who finally dont have any reason to boot Windows anymore.  I remember when I finally got rid of that dinosaur.  Feels good doesn't it!

---

### Post by bonsai4tim on 2010-02-18
I've been thrashing the certificate and error 61 problem for a week now. I've tried pasting the new certificates into the /cacert file (mutliple times). The first post on this thread fixed my problem:

cp /usr/share/ca-certificates/mozilla/* /usr/lib/ICAClient/keystore/cacerts/

thanks guys!!

tim

---

### Post by mnorwood154 on 2010-03-03
Instead of copying all the certs to a second location, you can just create symbolic links

sudo ln -s /usr/share/ca-certificates/mozilla/* /usr/lib/ICAClient/keystore/cacerts/

---

### Post by astarr on 2010-03-09
Works for me on Jaunty! Now I can work at home. Thanks ... I guess :rolleyes:

---

### Post by la3875 on 2010-04-20
Works on Lucid too!!!

---

### Post by evPaseo on 2010-09-01
Pascou22 thanks for the help. You're my hero!

---

### Post by mhamrud on 2010-12-11
Thank you Pascou22. Your advice resolved my problem instantly.:p

mhamrud

---

### Post by lightchaser on 2011-01-31
Thank you!

---

### Post by v.d.merwe@gmail.com on 2011-04-01
so for the newbies, open a terminal window.

Assuming you have Mozilla Firefox installed, this should work (usual - backup the target directory if you want)

sudo cp /usr/share/ca-certificates/mozilla/*.*  /usr/lib/ICAClient/keystore/cacerts/

---

### Post by nmw01223 on 2011-04-15
Copying certificates around doesn't work for me, I'm afraid. (sudo cp /usr/share/ca-certificates/mozilla/*  /usr/lib/ICAClient/keystore/cacerts).

It's GeoTrust I have the problem with: 'You have chosen not to trust "GeoTrust DV SSL CA" the issuer of the server's security certificate (SSL error 61)'. It's Firefox 3.6.10.

I can connect to the site from Windows via Firefox (3.6.16), but I've also heard of someone else having the same issue with a Mac and Firefox. The problem occurs not on logging in, but on trying to start an application.

Any helpful suggestions?

---

### Post by bradynathan on 2011-10-22
Recently installed the Citrix Receiver 12 on Kubuntu 11.10 64bit and received the same error message.  
[IMG]https://lh6.googleusercontent.com/-cKjQjlMektA/TqK35k6l20I/AAAAAAAAC6A/jwSP3Gy-NHE/s400/citrixreceiver.png[/IMG]

After a quick analysis of the packaged contents of the .deb file downloaded from Citrix I noticed they moved the cert store.  The following command, which copies the Firefox cert store to Citrix, should resolve the error with the version 12 of the Citrix Receiver.

 [COLOR=black][FONT=&quot]sudo cp /usr/share/ca-certificates/mozilla/* /opt/Citrix/ICAClient/keystore/cacerts/[/FONT][/COLOR]

---

### Post by nederland on 2011-12-29
Hi,
I have modified the script (different installation directory and some cert names) from Peter Dyson and it has worked for Ubuntu 10.04 installation.
Cheers!

#!/bin/bash
#
# Version: 0.2
# Author: Peter Dyson <pete@geekpete.com>
# Modified by <nederland@mail.ru> for Ubuntu 10.04
# Purpose: A workaround until Citrix gets their act together and packages up a better install script.
# What it does: downloads and installs Thawte root certs in the required location.
#
# CHANGELOG
#            v0.1 - initial release
#   20090522 v0.2 - Thawte dropped a new cert zip file on their site, uses different subdirs, broke the script, fixed.
#

# change the install dir to be whatever you need, you may have used a local dir in your homedir,etc.
CERTINSTALLDIR="/opt/Citrix/ICAClient/keystore/cacerts"
# CERTINSTALLDIR="/usr/lib/ICAClient/keystore/cacerts"
# CERTINSTALLDIR="/usr/lib/ssl/certs"
STARTDIR=$PWD

#echo $CERTINSTALLDIR
#exit
echo Current directory is: $STARTDIR
echo Creating temp download dir in $STARTDIR...
mkdir cert_download
cd cert_download
echo Fetching Thawte Root Certs...
wget [https://www.verisign.com/support/thawte-roots.zip](https://www.verisign.com/support/thawte-roots.zip)
echo Unzipping Thawte Root Certs...
unzip thawte-roots.zip
echo Copying Thawte Root Certs to $CERTINSTALLDIR and renaming them...
echo This step uses sudo, enter your user password to run this step as root:
sudo cp "Thawte Root Certificates/Thawte Timestamping CA/Thawte Timestamping CA.cer" $CERTINSTALLDIR/ThawteTimestampingCA.crt
sudo cp "Thawte Root Certificates/thawte SGC Root CA/Class 3 Public Primary Certification Authority.cer" $CERTINSTALLDIR/Class3PublicPrimaryCertificationAuthority.crt
sudo cp "Thawte Root Certificates/thawte Server CA/Thawte Server CA.cer" $CERTINSTALLDIR/ThawteServerCA.crt
sudo cp "Thawte Root Certificates/thawte Primary Root CA - G2 (ECC)/thawte Primary Root CA - G2_ECC.cer" $CERTINSTALLDIR/thawtePrimaryRootCAG2_ECC.crt
sudo cp "Thawte Root Certificates/thawte Primary Root CA - G1 (EV)/thawte_Primary_Root_CA.cer" $CERTINSTALLDIR/thawte_Primary_Root_CA.crt
sudo cp "Thawte Root Certificates/thawte Premium Server CA/Thawte Premium Server CA.cer" $CERTINSTALLDIR/ThawtePremiumServerCA.crt
sudo cp "Thawte Root Certificates/Thawte Personal Premium CA/Thawte Personal Premium CA.cer" $CERTINSTALLDIR/ThawtePersonalPremiumCA.crt
sudo cp "Thawte Root Certificates/Thawte Personal Freemail CA/Thawte Personal Freemail CA.cer" $CERTINSTALLDIR/ThawtePersonalFreemailCA.crt
sudo cp "Thawte Root Certificates/Thawte Personal Basic CA/Thawte Personal Basic CA.cer" $CERTINSTALLDIR/ThawtePersonalBasicCA.crt

cd $STARTDIR
echo Removing temp download dir...
rm -rf cert_download
echo Citrix SSL Cert fix complete!

---

### Post by leigh_j_d on 2012-09-25
Just got Citrix working on 12.04, seems the install location had changed so I had to copy using the following command

sudo cp /usr/share/ca-certificates/mozilla/* /opt/Citrix/ICAClient/keystore/cacerts/

and all is working as it should.

ps I found the install location simply by searching for the ICAClient folder

---

