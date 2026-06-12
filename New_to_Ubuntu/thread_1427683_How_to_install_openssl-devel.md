---
title: "How to install openssl-devel"
date: 2010-03-11
forum: New to Ubuntu
---

### Post by smillion on 2010-03-11
Really starting to lose faith in Ubuntu. I think it's an OS better useful for people with a high knowledge in computers because there are too many commands and drivers which I have absolute no clue about.

Anyway I'm trying to install openssl-devel. Looked at other posts and forums and they all say either look into synaptics or type 'sudo apt-get install libssl-dev'. 

Typing 'sudo apt-get install libssl-dev' ends with this 
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

When I look into synaptics I get nothing. I still don't know what all that crap in my synaptics package manager is.

Apologies for being rude but I'm really starting to get impatient since everyday for the past few weeks I've had to install something new on ubuntu just to get things working.

---

### Post by tom.swartz07 on 2010-03-11
> **smillion said:**
> Really starting to lose faith in Ubuntu. I think it's an OS better useful for people with a high knowledge in computers because there are too many commands and drivers which I have absolute no clue about.

Anyway I'm trying to install openssl-devel. Looked at other posts and forums and they all say either look into synaptics or type 'sudo apt-get install libssl-dev'. 

Typing 'sudo apt-get install libssl-dev' ends with this 
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

When I look into synaptics I get nothing. I still don't know what all that crap in my synaptics package manager is.

Apologies for being rude but I'm really starting to get impatient since everyday for the past few weeks I've had to install something new on ubuntu just to get things working.

Alrighty. No bigs.

The reason that youre getting that error message is because you have more than 1 application installer program open at once.

Restart your computer just to make sure that you dont have any runaway processes from your update manager that may cause it to seize up.

Now, go to System>Administration>Synaptic Package Manager. This program is used to install very specific applications, such as your libssl-dev package. 

It will prompt for a password, then it will open. The interface is a bit daunting but its okay once you get used to it. Near the top middle, theres a text box used for search- type in libssl-dev and look in the list below. It should be listed there; Click the checkbox next to it and select 'Install'. Now click apply.

Youre done!

---

### Post by smillion on 2010-03-12
Hi Tom added 3 attachments. 

2 are from the Synaptics. I double clicked on libssl-dev and the second attachment shows what appeared.

The third attachment is from my university regarding why I need openssl-devel.

Thanks

---

### Post by tom.swartz07 on 2010-03-12
> **smillion said:**
> Hi Tom added 3 attachments. 

2 are from the Synaptics. I double clicked on libssl-dev and the second attachment shows what appeared.

The third attachment is from my university regarding why I need openssl-devel.

Thanks

Yep, The additional package is needed for the application to work. Just click to mark it and apply it. Youll be all set then!

---

