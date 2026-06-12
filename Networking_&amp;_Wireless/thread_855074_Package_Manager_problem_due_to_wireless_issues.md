---
title: "Package Manager problem due to wireless issues"
date: 2008-07-10
forum: Networking &amp; Wireless
---

### Post by subushady on 2008-07-10
Hi ,
I have installed Ubuntu Hardy 8.04 and updated a lot of stuff.Now the problem is that:
I have access to Wi-fi which is restricted. Meaning, if i open firefox and type any url, a pop up comes and on giving the username and password, i am able to surf and download.
But when i open package manager and try installing a product, it gives error as its not able to connect to internet.
Also throught terminal windows ping Google does not work.

But i am able to manually download the packages (deb files) and install them as through the browser there is authentication.
Is there any way i can supply the username and password for the connection.

Thanks,
Subu

---

### Post by rxtx on 2008-07-10
[This]("http://beans.seartipy.com/2006/11/03/simple-way-to-update-ubuntu-edgy-with-slowno-internet-connection/") might be of use. (Via, [this]("http://ubuntuforums.org/showthread.php?t=855063") post).

Also, SOME software is available from the Ubuntu CDrom if you specify so in software sources.

---

### Post by subushady on 2008-07-10
Actually my problem is that through firefox i can download packages through packages.ubuntu.com (the wi-fi i access is restricted and required authentication which pops up once i type the url in firefox)
but through package manager i am not able to download and install as i guess i am not getting authenticated
also throught terminal i am not able to access the net.

so, i was wondering that if there is any way to get authenticated through the terminal and specify the username and password in the connection settings of wi-fi

thanks,
subu.


> **rxtx said:**
> [This]("http://beans.seartipy.com/2006/11/03/simple-way-to-update-ubuntu-edgy-with-slowno-internet-connection/") might be of use. (Via, [this]("http://ubuntuforums.org/showthread.php?t=855063") post).

Also, SOME software is available from the Ubuntu CDrom if you specify so in software sources.

---

### Post by rxtx on 2008-07-10
Just a random thing worth trying. What happens with wget in the terminal? Have you tried using apt-get from the terminal?

---

### Post by subushady on 2008-07-11
I will try wget...apt-get install does not work as it does not get the connection, i guess i need to ask the network administrator who has set the wi-fi network.

Thanks,
Subu.

> **rxtx said:**
> Just a random thing worth trying. What happens with wget in the terminal? Have you tried using apt-get from the terminal?

---

