---
title: "Failed to download packages"
date: 2009-03-06
forum: New to Ubuntu
---

### Post by walidg on 2009-03-06
Hi

I'm using Ubuntu 8.10 installed on a vmware machine.
I connect to The Internet through a proxy.
I'm trying to install vmware tools 
so I followed this tutorial:
[http://ubuntu-tutorials.com/2007/10/02/how-to-install-vmware-tools-on-ubuntu-guests/](http://ubuntu-tutorials.com/2007/10/02/how-to-install-vmware-tools-on-ubuntu-guests/)
I'm having these errors after trying this command:
sudo aptitude install build-essential linux-headers-$(uname -r)

here are the errors:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following NEW packages will be installed:
  build-essential dpkg-dev{a} g++{a} g++-4.3{a} libstdc++6-4.3-dev{a} 
  patch{a} 
0 packages upgraded, 6 newly installed, 0 to remove and 0 not upgraded.
Need to get 6203kB of archives. After unpacking 21.3MB will be used.
Do you want to continue? [Y/n/?] y
WARNING: untrusted versions of the following packages will be installed!

Untrusted packages could compromise your system's security.
You should only proceed with the installation if you are certain that
this is what you want to do.

  libstdc++6-4.3-dev g++-4.3 g++ dpkg-dev patch build-essential 

Do you want to ignore this warning and proceed anyway?
To continue, enter "Yes"; to abort, enter "No": yes
Writing extended state information... Done
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main libstdc++6-4.3-dev 4.3.2-1ubuntu11
  Could not resolve 'mail'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main g++-4.3 4.3.2-1ubuntu11
  Could not resolve 'mail'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main g++ 4:4.3.1-1ubuntu2
  Could not resolve 'mail'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main patch 2.5.9-5
  Could not resolve 'mail'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main dpkg-dev 1.14.20ubuntu6
  Could not resolve 'mail'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main build-essential 11.4
  Could not resolve 'mail'
E: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.3/libstdc++6-4.3-dev_4.3.2-1ubuntu11_i386.deb:](http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.3/libstdc++6-4.3-dev_4.3.2-1ubuntu11_i386.deb:) Could not resolve 'mail'
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done

Any idea would be very helpful
thank you

---

### Post by JoshuaRL on 2009-03-06
Just as a first try, do the following:
```

sudo dpkg --configure -a
sudo apt-get install -f
sudo apt-get update
sudo apt-get upgrade

```
Then, try that other install again.

---

### Post by walidg on 2009-03-06
> **JoshuaRL said:**
> Just as a first try, do the following:
```

sudo dpkg --configure -a
sudo apt-get install -f
sudo apt-get update
sudo apt-get upgrade

```
Then, try that other install again.

Thank you for your reply
I got this after sudo apt-get update

Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main Translation-en_US
  Connection timed out

I think this is due to ISA/proxy connection

---

### Post by shredder12 on 2009-03-06
well, can you at least ping these sites..or any other..
i believe you have already put the proxy settings.. 
may you should also enter the proxy settings in synaptic..
synaptic->setting->preferences->network..
hope this helps..

---

### Post by walidg on 2009-03-10
Now that's ok
The problem was ISA proxy which I configured using ntlmaps package

[http://www.linuxquestions.org/linux/answers/Networking](http://www.linuxquestions.org/linux/answers/Networking)
/HOWTO_Install_and_Configure_NTLMaps_for_use_with_an_ISA_Proxy
:D

---

