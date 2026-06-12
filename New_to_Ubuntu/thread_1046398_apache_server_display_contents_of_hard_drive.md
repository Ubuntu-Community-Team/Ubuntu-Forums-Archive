---
title: "apache server display contents of hard drive"
date: 2009-01-21
forum: New to Ubuntu
---

### Post by benfindlay on 2009-01-21
Ok, so I've got apache up and running on my server (checked by putting an index.html file into /var/www/ and accessing it via another machine on the network) and I want to access the machine's hard drive via http (through firefox basically) to download large files across the network to be worked on on different computers. How would I go about setting apache to display the contents of a specific directory, showing all subfolders and files etc present?

Would this be easier if the machines connecting were set more as remote terminals to connect to the server?

Thanks

Ben

---

### Post by cariboo on 2009-01-21
you may just want to create a symlink in your /var/www directory to the directory that the files are located in, for example:

```
sudo ln -s /home/directory/big_files /var/www/big_files
```

I would suggest only doing the above for use on your internal network. If your server is going to show it's face to the world, sftp/scp would be a much better choice.

Jim

---

### Post by benfindlay on 2009-01-21
Hi, thanks for the quick reply! Yeah, the server is on a wired-only, closed network, so security isn't really that big an issue!

Thats exactly what I'm looking for, thanks! I take it I can just add multiple symbolic links to the location and they'll all show up like a directory listing?

Thanks!

Ben

---

### Post by benfindlay on 2009-01-21
Your symlink idea just made another thought occur to me. Is it possible to create a symlink (or any other type of link) to a folder on another machine on the network so that it shows up on my local machine in the directory structure?

---

### Post by Coreigh on 2009-01-21
I believe it is better not to use a sym-link and use a <Directory> profile in your sites-available config (usually /etcapache2/sites-available/default << default is the name of the config file). Using a <Directory> statment gives you control over many attributes regarding how and what file to show, including whether you want to require an index page or just show a directory listing. You want to show a directory listing. I am sorry I am not a whiz at Apache setup and I didn't find any easy links with a quick search but there are lots out there. You can probably start with Apache's own documentation;
[http://httpd.apache.org/docs/2.0/](http://httpd.apache.org/docs/2.0/)

Have fun!

---

