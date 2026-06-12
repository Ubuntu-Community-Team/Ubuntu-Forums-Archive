---
title: "Need Help in configuring network connections"
date: 2011-04-07
forum: New to Ubuntu
---

### Post by sandy0594 on 2011-04-07
Hi all,i am too new for linux..I installed Ubuntu 10.10 desktop edition from windows.When i am trying to configure network connections i am facing problems

```


udo pppoeconf

Sorry,no working ethernet card could be found.If you do have an interface card which was not autodetected so far,you probably wish to load the driver manually using the modconf utility.Run modconf now?  

 /usr/sbin/pppoeconf: 523: modconf: not found
 
 Ifconfig
  
   Link encap:Local Loopback  
            inet addr:127.0.0.1  Mask:255.0.0.0
            inet6 addr: ::1/128 Scope:Host
            UP LOOPBACK RUNNING  MTU:16436  Metric:1
            RX packets:20 errors:0 dropped:0 overruns:0 frame:0
            TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:0 
              RX bytes:1304 (1.3 KB)  TX bytes:1304 (1.3 KB)


  
lspci -nn | grep Ethernet

  01:00.0 Ethernet controller [0200]: Atheros Communications Device [1969:1083] (rev c0)


```

```


sudo lshw -C network

*-network UNCLAIMED     
       description: Ethernet controller
       product: Atheros Communications
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:01:00.0
       version: c0
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list
       configuration: latency=0
       resources: memory:febc0000-febfffff ioport:ec00(size=128)


```

So,by searching some posts..i downloaded AR81Family-linux-v1.0.1.14 and  AR81Family-linux-v1-1.0.1.14.patch.But,what disgusting is i couldn't  install them due to some errors

```


Makefile:105: *** Linux kernel source not configured - missing autoconf.h.  Stop.
   
  sandy@ubuntu:~$ patch -p1  /media/18D80590D8056CF6/Documents and Settings/Sandy/My Documents/Downloads/AR81Family-linux-v1-1.0.1.14.patch/AR81Family-linux-v1-1.0.1.14.patch
  The program 'patch' is currently not installed.  You can install it by typing:
  sudo apt-get install patch
   
  sandy@ubuntu:~$ sudo apt-get install patch
  Reading package lists... Done
  Building dependency tree       
  Reading state information... Done
  E: Unable to locate package patch


```

---

### Post by alphacrucis2 on 2011-04-07
> **sandy0594 said:**
> Hi all,i am too new for linux..I installed Ubuntu 10.10 desktop edition from windows.When i am trying to configure network connections i am facing problems

```


udo pppoeconf

Sorry,no working ethernet card could be found.If you do have an interface card which was not autodetected so far,you probably wish to load the driver manually using the modconf utility.Run modconf now?  

 /usr/sbin/pppoeconf: 523: modconf: not found
 
 Ifconfig
  
   Link encap:Local Loopback  
            inet addr:127.0.0.1  Mask:255.0.0.0
            inet6 addr: ::1/128 Scope:Host
            UP LOOPBACK RUNNING  MTU:16436  Metric:1
            RX packets:20 errors:0 dropped:0 overruns:0 frame:0
            TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:0 
              RX bytes:1304 (1.3 KB)  TX bytes:1304 (1.3 KB)


  
lspci -nn | grep Ethernet

  01:00.0 Ethernet controller [0200]: Atheros Communications Device [1969:1083] (rev c0)


```

```


sudo lshw -C network

*-network UNCLAIMED     
       description: Ethernet controller
       product: Atheros Communications
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:01:00.0
       version: c0
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list
       configuration: latency=0
       resources: memory:febc0000-febfffff ioport:ec00(size=128)


```

So,by searching some posts..i downloaded AR81Family-linux-v1.0.1.14 and  AR81Family-linux-v1-1.0.1.14.patch.But,what disgusting is i couldn't  install them due to some errors

```


Makefile:105: *** Linux kernel source not configured - missing autoconf.h.  Stop.
   
  sandy@ubuntu:~$ patch -p1  /media/18D80590D8056CF6/Documents and Settings/Sandy/My Documents/Downloads/AR81Family-linux-v1-1.0.1.14.patch/AR81Family-linux-v1-1.0.1.14.patch
  The program 'patch' is currently not installed.  You can install it by typing:
  sudo apt-get install patch
   
  sandy@ubuntu:~$ sudo apt-get install patch
  Reading package lists... Done
  Building dependency tree       
  Reading state information... Done
  E: Unable to locate package patch


```

Try this first:

```
sudo apt-get install build-essential
```

That should get you the missing bits you need for patching/compiling.

---

### Post by sandy0594 on 2011-04-07
I tried as per ur suggestion,here are the results:

```


 sandy@ubuntu:~$ sudo apt-get install build-essential
  [sudo] password for sandy: 
  Reading package lists... Done
  Building dependency tree       
  Reading state information... Done
  E: Unable to locate package build-essential
  


```

---

### Post by Hippytaff on 2011-04-07
If you can't get online you can't do```
sudo apt-get install ...
``` you will need to download the package via a pc that can get online, and copy it to your pc that  can't get online and install it that way. There is guidance [here ]("https://help.ubuntu.com/community/InstallingSoftware#Installing%20downloaded%20packages")to help you do that

---

### Post by sandy0594 on 2011-04-07
Can u be more specific of which package i need to install,i am running windows and ubuntu on same pc..I am on windows xp now and online

---

### Post by Hippytaff on 2011-04-07
Do you have livecd? if so you should be able to install build-essential like this```
sudo apt-cdrom add
sudo apt-get update
sudo apt-get install build-essential
```

---

### Post by sandy0594 on 2011-04-07
No,i installed ubuntu using windows installer **wubi**

---

### Post by sandy0594 on 2011-04-07
with the guidance from [https://help.ubuntu.com/community/InstallingSoftware#Installing%20downloaded%20packages](https://help.ubuntu.com/community/InstallingSoftware#Installing%20downloaded%20packages)

I got synaptic script which is below,i viewed from firefox browser

```


wget -c http://security.ubuntu.com/ubuntu/pool/main/k/krb5/libgssrpc4_1.8.1+dfsg-5ubuntu0.1_i386.deb wget -c http://security.ubuntu.com/ubuntu/pool/main/k/krb5/libkadm5clnt-mit7_1.8.1+dfsg-5ubuntu0.1_i386.deb wget -c http://security.ubuntu.com/ubuntu/pool/main/k/krb5/libkdb5-4_1.8.1+dfsg-5ubuntu0.1_i386.deb wget -c http://security.ubuntu.com/ubuntu/pool/main/k/krb5/libkadm5srv-mit7_1.8.1+dfsg-5ubuntu0.1_i386.deb wget -c http://security.ubuntu.com/ubuntu/pool/main/k/krb5/krb5-doc_1.8.1+dfsg-5ubuntu0.1_all.deb wget -c http://security.ubuntu.com/ubuntu/pool/main/o/openssl/openssl-doc_0.9.8o-1ubuntu4.1_all.deb wget -c http://security.ubuntu.com/ubuntu/pool/main/k/krb5/libkrb5-dbg_1.8.1+dfsg-5ubuntu0.1_i386.deb wget -c http://security.ubuntu.com/ubuntu/pool/main/o/openssl/libssl0.9.8-dbg_0.9.8o-1ubuntu4.1_i386.deb


```

---

### Post by alphacrucis2 on 2011-04-07
> **sandy0594 said:**
> with the guidance from [https://help.ubuntu.com/community/InstallingSoftware#Installing%20downloaded%20packages](https://help.ubuntu.com/community/InstallingSoftware#Installing%20downloaded%20packages)

I got synaptic script which is below,i viewed from firefox browser

```


wget -c http://security.ubuntu.com/ubuntu/pool/main/k/krb5/libgssrpc4_1.8.1+dfsg-5ubuntu0.1_i386.deb wget -c http://security.ubuntu.com/ubuntu/pool/main/k/krb5/libkadm5clnt-mit7_1.8.1+dfsg-5ubuntu0.1_i386.deb wget -c http://security.ubuntu.com/ubuntu/pool/main/k/krb5/libkdb5-4_1.8.1+dfsg-5ubuntu0.1_i386.deb wget -c http://security.ubuntu.com/ubuntu/pool/main/k/krb5/libkadm5srv-mit7_1.8.1+dfsg-5ubuntu0.1_i386.deb wget -c http://security.ubuntu.com/ubuntu/pool/main/k/krb5/krb5-doc_1.8.1+dfsg-5ubuntu0.1_all.deb wget -c http://security.ubuntu.com/ubuntu/pool/main/o/openssl/openssl-doc_0.9.8o-1ubuntu4.1_all.deb wget -c http://security.ubuntu.com/ubuntu/pool/main/k/krb5/libkrb5-dbg_1.8.1+dfsg-5ubuntu0.1_i386.deb wget -c http://security.ubuntu.com/ubuntu/pool/main/o/openssl/libssl0.9.8-dbg_0.9.8o-1ubuntu4.1_i386.deb


```

You could just download the deb packages under windows. Ubuntu should be able to access the downloaded files in the windows NTFS partition. For example, the Maverick deb is here:

[http://packages.ubuntu.com/maverick/build-essential]("http://packages.ubuntu.com/maverick/build-essential")

Download the package as well as any dependencies if necessary. 
Create a folder under Ubuntu eg /home/<my user>/debs and copy all the downloaded deb files from the windows partition to that folder.

You can install multiple deb files like this:

```
cd debs
sudo dpkg -i *.deb
```

dpkg will tell you if you are missing any dependencies.

---

### Post by sandy0594 on 2011-04-08
thank you,i installed the required packages and configured my n/w connections..can anyone say me how to know if any package is missing to be installed..in synaptec package manager the list is too huge which is quite cumbersome to locate..is there any command or like that by which we can know what all the necessary packages are missing

---

### Post by alphacrucis2 on 2011-04-08
> **sandy0594 said:**
> thank you,i installed the required packages and configured my n/w connections..can anyone say me how to know if any package is missing to be installed..in synaptec package manager the list is too huge which is quite cumbersome to locate..is there any command or like that by which we can know what all the necessary packages are missing


If you have a network connection running, you don't normally need to know what the dependencies are as your choice of apt-get, synaptic or ubuntu software centre should automatically pull in all required dependencies. Under synaptic you should be able to right click on the package in question and select properties. Then click the dependencies tab to get a list of the dependencies.

---

### Post by sandy0594 on 2011-04-08
That looks fine for me..thanks for the reply :)

---

