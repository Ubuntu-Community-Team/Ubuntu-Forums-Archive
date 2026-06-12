---
title: "How to keep lottanzb up-to -date???"
date: 2009-05-17
forum: New to Ubuntu
---

### Post by mikodo on 2009-05-17
I have installed LottaNZB on top of HellaNZB. From the LottaNZB download site:  [http://www.lottanzb.org/downloads/ubuntu/](http://www.lottanzb.org/downloads/ubuntu/)  it states you can easily keep LottaNZB up to date by following the directions below.

When I copy and paste the command into terminal I get the further message in terminal;(see bottom). 

Can anyone tell me what to do, to able this update process to work? Desktop is replaced with ************ .

--------------------------------------------------------------------------

How to easily keep LottaNZB up-to-date

If you don’t want to visit this site and install the above package by hand everytime a new version of LottaNZB is released, you can add our PPA (Personal Package Archive) to your software sources.

You can do this by copying and pasting the following command into the terminal:

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 93A5BC72

source /etc/lsb-release

echo "deb [http://ppa.launchpad.net/lottanzb/ppa/ubuntu](http://ppa.launchpad.net/lottanzb/ppa/ubuntu) $DISTRIB_CODENAME main" | sudo tee /etc/apt/sources.list.d/lottanzb-ppa.list

From now on, LottaNZB updates will be displayed in the update manager along with the other Ubuntu updates.

--------------------------------------------------------------------------

TERMINAL

**********-desktop:~$ sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 93A5BC72
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --recv-keys --keyserver keyserver.ubuntu.com 93A5BC72
gpg: requesting key 93A5BC72 from hkp server keyserver.ubuntu.com
gpgkeys: HTTP fetch error 7: couldn't connect to host
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0
***********-desktop:~$ 
***********-desktop:~$ source /etc/lsb-release
***********-desktop:~$ 
***********-desktop:~$ echo "deb [http://ppa.launchpad.net/lottanzb/ppa/ubuntu](http://ppa.launchpad.net/lottanzb/ppa/ubuntu) $DISTRIB_CODENAME main" | sudo tee /etc/apt/sources.list.d/lottanzb-ppa.list
deb [http://ppa.launchpad.net/lottanzb/ppa/ubuntu](http://ppa.launchpad.net/lottanzb/ppa/ubuntu) hardy main
***********-desktop:~$ 

-------------------------------------------------------------------------

Thank you,

mikodo

---

### Post by nhasian on 2009-05-17
copy and save the following code to a file named lottanzb.key:

```
-----BEGIN PGP PUBLIC KEY BLOCK-----
Version: SKS 1.0.10

mI0ESYxxzwEEAK/v8Eu3V00RX7CtjqfF7WSXWGKVWpGUDbFNiWWJ5XKTYr9jFDwVGss0+r0y
bLAlXHrZE+7iVwUHRbW/mHXQyKoSamjrbl40IWcUla2HEqcQn0/mhTXxSRVKpSjDwaEh8Af8
pkbOHrJSCegBJjY+XUMUHTQj8qDAfwQNeVmKO6DnABEBAAG0K0xhdW5jaHBhZCBQUEEgZm9y
IExvdHRhTlpCIERldmVsb3BtZW50IFRlYW2ItgQTAQIAIAUCSYxxzwIbAwYLCQgHAwIEFQII
AwQWAgMBAh4BAheAAAoJELc12w6Tpbxym7kD/0ohsS9jhlVr+ZICcEA90s3JXq3g6OVwQtat
e/2FR2clg/7NgqWuV5WHMBoT4tC0A+A63ByZT1ll5g4JbxVYO8p2S7o4RiMxPGOR6IZo7Oj+
hMpQ+wWxk8c2G02ggaT20ufFdbpFIhEpa6VKoJNQQfRg9dRrqmn73vOaR0Cl/aS9
=QAns
-----END PGP PUBLIC KEY BLOCK-----

```

Click on System->Administration->Software Sources, then click on Third Party Software.

click the ADD button and add:


```

deb http://ppa.launchpad.net/lottanzb/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/lottanzb/ppa/ubuntu jaunty main
```

if your using hardy just replace the jaunty in the lines with hardy.

click on Authentication, click import key file and choose the lottanzb.key you saved earlier.

now your lottanzb should stay up to date.

---

### Post by mikodo on 2009-05-17
Thank you for your detailed post! I will be trying to follow it at a later time. If I have trouble following, I will ask more questions.

Thanks again,

Mikodo

Canada

---

### Post by Lantash on 2009-05-17
Hi mikodo,

in fact, only the first command did not work, the other two have worked just fine. The first one makes sure that your computer can verify that the LottaNZB packages have not been altered in some way (that's what the key is for).

For an unknown reason, your computer could not connect to the Ubuntu key server. You could try it again or create the file with the key mentioned by nhasian and import it as described. You don't need to add the two sources anymore though.

Regards,
Lantash

---

