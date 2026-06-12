---
title: "How can I access my school's server?"
date: 2009-11-05
forum: New to Ubuntu
---

### Post by raketbror on 2009-11-05
I just sold one of my laptops, so I am currently using an Acer netbook with Ubuntu. I want to connect to the school server, on which we host shared files for homework etc. On my old Windows Vista laptop, I could just use the "Run"-tool and type "\\servername" and then I would be prompted to enter my username and password and I would be able to browse the server through Windows Explorer. 
Now, how do I do this in Ubuntu? 
Any help will be greatly appreciated!

PS. I know my english sucks.

---

### Post by bodhi.zazen on 2009-11-05
Open a terminal and install smbfs

```
sudo apt-get install smbfs
```

Then make a mount point

```
sudo mkdir /media/school
```

And finally mount your share

```
sudo mount //your_server/Share_name /media/school -o user=user_name
```

Or you can use nautilus, go to places, connect to a server.

---

### Post by RJ12 on 2009-11-05
> **bodhi.zazen said:**
> Open a terminal and install smbfs

```
sudo apt-get install smbfs
```

Then make a mount point

```
sudo mkdir /media/school
```

And finally mount your share

```
sudo mount //your_server/Share_name /media/school -o user=user_name
```

Or you can use nautilus, go to places, connect to a server.

+2
I was gonna say the places but you beat me:lolflag:

---

### Post by phillw on 2009-11-05
> **RJ12 said:**
> +2
I was gonna say the places but you beat me:lolflag:


You're going to have to be quicker to beat bhodi !!!!

:popcorn:

---

