---
title: "How to Install Ubuntu Using Already Downloaded Packages"
date: 2009-05-04
forum: New to Ubuntu
---

### Post by bernardolopes on 2009-05-04
Hello,

I have download and installed a bunch of packages and softwares like: codecs, plugins, Firefox add-ons, IDEs, etc. So I costumized my Ubuntu 9.04 system to my likeness.

And I have a separate partition for the Home directory.

I would like to know how can I make a new installation of Ubuntu and after that "restore" all my packages, configurations and softwares. How to preserve my costumization on a new installation without download all of the content again?

I don't know if that's a too broad question and I aplogize for my lack of knowledge on Linux/Ubuntu.

I, of course, have searched the Internet but only found tutorials on how to install Ubuntu with a separate Home folder.

Maybe I used the wrong search terms.

Any help will be deeply appreciated.

Thanks.

---

### Post by Bradtek on 2009-05-04
This might be what you're looking for

[http://www.remastersys.klikit-linux.com/ubuntu.html](http://www.remastersys.klikit-linux.com/ubuntu.html)

---

### Post by oldos2er on 2009-05-04
Take a look at [http://www.geekconnection.org/remastersys/remastersystool.html](http://www.geekconnection.org/remastersys/remastersystool.html)

---

### Post by wiznillyp on 2009-05-04
> **Bradtek said:**
> This might be what you're looking for

[http://www.remastersys.klikit-linux.com/ubuntu.html](http://www.remastersys.klikit-linux.com/ubuntu.html)

> **oldos2er said:**
> Take a look at [http://www.geekconnection.org/remastersys/remastersystool.html](http://www.geekconnection.org/remastersys/remastersystool.html)Both links reference the same software FYI.

I am using the software right now and I really like it.

Just add: 
# Remastersys
deb [http://www.geekconnection.org/remastersys/repository](http://www.geekconnection.org/remastersys/repository) ubuntu/

to the /etc/apt/sources.list

Then execute:

sudo apt-get update
sudo apt-get install remastersys
sudo remastersys backup

This will create an ISO in your /home/remastersys/remastersys folder

Enjoy!!

---

### Post by Jimmynemo2 on 2009-05-04
Just checked those out- holy smokes, very cool!

Good to know about.

---

### Post by bernardolopes on 2009-05-04
Yes, that did the job.

Thanks oldos2er and Bradtek. And wiznillyp.

---

