---
title: "[SOLVED] Connect to local intranet."
date: 2008-09-22
forum: Networking &amp; Wireless
---

### Post by theDaveTheRave on 2008-09-22
Dear All.

I've just noticed something rather strange.

I'm connected to the internet via my works ethernet connection, which is great. But I've just realised I can see the network (via ifconfig) but can't connect to it in the same way I would if I was using a windows pc.

I KNOW THAT LINUX ISN'T WINDOZE.... but... how do I browse through the network shares and printers etc?

I want to do this so as to create automatic backups / mirror between my "test" MySQL database and my laptop.... then I know that I will be able to create the same thing in the final live environment, from the server to a second backup pc elsewhere in the department.

Also I will be then able to work on the database and stuff and just update the files between what I have done at home and what needs to be changed for the live environment etc.

tanks for the input,

ps, where are my database files kept in the MySQL instalation, this is in reference to both windows (ie work desktop) and ubuntu as I can't find them.... currently I only have tables and stuff, as I want to write a GUI front end to access the info for adding data etc.

Thanks in advance

---

### Post by timcredible on 2008-09-22
install samba via synaptic, then places->network to view windows shares.

---

### Post by theDaveTheRave on 2008-09-22
timcredible,

Thanks, as I only wanted to view the windows share from my pc, initally I assumed I didn't need samba!!

I'm all installed and ready to head home.

I'll test tomorrow

cheers for the help

Dave

---

### Post by theDaveTheRave on 2008-09-26
Hooray finaly.

I've connected to the windoze pc that holds the first instalment of my test database! Success, well partialy!

Now all I have to do is confirm that I can get to the samba share on my laptop from the windoze terminal.

Oddly enough when I did this previously with a load of music files onto my desktop and connected with my wife's Windoze laptop, everything went beautifully!

This time however it seems a little more tricky!

Well for now I am half solved!

Dave

---

