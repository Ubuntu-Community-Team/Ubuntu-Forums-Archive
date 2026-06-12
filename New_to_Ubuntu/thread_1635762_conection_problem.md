---
title: "conection problem"
date: 2010-12-02
forum: New to Ubuntu
---

### Post by skt.diaz on 2010-12-02
i setup a mobile broadband connection using my nokia e71. i connected successfully but synaptics cant download any packages for some reason. firefox is running perfectly and i am able to  open webpages. can anyone help,please?

---

### Post by Zookalicious on 2010-12-02
Hi skt.diaz, could you please type 
```
sudo apt-get update
sudo apt-get install "name of package you are trying to install"

```
into the terminal and let us know what comes from that? make sure not to put quotation marks in the above command (you probably know that, but just in case).

---

### Post by skymera on 2010-12-02
Hi,

I'm guess you're tethering your mobile connection through your phone either wireless or USB?

USB tethering I'm sure needs software to run which I'm certain isn't Linux compatible. Wireless tether makes your phone act as an Access Point, like I do with my Android phone.

My knowledge on this area is a little grey, but i'll help as much as possible.

---

### Post by Zookalicious on 2010-12-02
> **skymera said:**
> Hi,

I'm guess you're tethering your mobile connection through your phone either wireless or USB?

USB tethering I'm sure needs software to run which I'm certain isn't Linux compatible. Wireless tether makes your phone act as an Access Point, like I do with my Android phone.

My knowledge on this area is a little grey, but i'll help as much as possible.

He can browse the web. So I don't think it's a connectivity issue.

---

### Post by skymera on 2010-12-02
> **Zookalicious said:**
> He can browse the web. So I don't think it's a connectivity issue.

ah yes, I misread. I thought it said "not able to laod web pages".

Disregard my post.

OP: Could you go to System > Administration > Software Sources

Click the drop down and change the server. Then choose to "reload"

---

### Post by skt.diaz on 2010-12-03
i tried it again today and its working this time. Dont knw wht happnd. I am able to downld packages now. Thnx for replyin everone

---

