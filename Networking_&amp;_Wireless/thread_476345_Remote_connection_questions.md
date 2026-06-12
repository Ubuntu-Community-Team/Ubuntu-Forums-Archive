---
title: "Remote connection questions"
date: 2007-06-17
forum: Networking &amp; Wireless
---

### Post by kackland on 2007-06-17
Hi

I'm trying to learn PHP at the moment. 
I have a Ubuntu LAMP server. I want to connect to this server from my Ubuntu desktop machine and create some test php files.

I'm going to use Screem.

When I try to open a site it asks me for the URL. I dont know how to connect.

How do I setup a connection to the server with the right permissions for me.

Because I can't edit or create files at the moment I decided to install php on my desktop. Php can't be configured correctly because I created a .php file which just wanted to download. I know it's a separate subject but I'd like to know what I'm doing on both setups.

Thanks

---

### Post by Biggus on 2007-06-17
It's not an exact answer to your question, but I do a similar sort of thing on my own box at home.

I just run an apache server on my local box, with screem installed on it as well.

I just copy the pages I create into the Apache directory (/var/www), open up Epiphany, and type in my IP address to connect to it. (I could probably use localhost, or 127.0.0.1 as well, but I've honestly never tried it)

---

### Post by silverglade00 on 2007-06-17
What you are looking for is sshd on the server. It lets you log in to a command line remotely. However, it is possibleto set it up so that you can type the name of a GUI program and it will pop up on your local screen! Good stuff. You can also use the Applications -> Terminal Server Client to make a connection that will let you drag and drop files. You use your normal login for the server machine when it asks for it.

---

### Post by kackland on 2007-06-18
Thanks Biggus.

I'm assuming the the only user with read and write to the apache server is root and that's the reason why you have to copy it to the /var/www later.

I have played about with Places, Connect to a server. i think that this can be configured to get proper access to the /var/www directory if you use gksu nautilus. Not had any success yet.

Screem can open a website - so it should be possible.

---

### Post by Biggus on 2007-06-19
Yeah, I have my little Apache set up so that it's only root which can write to it.

Unfortunately, I've never used the facility to connect directly to a server in 'Screem', although I have done that exact thing in the past, using Dreamweaver running in wine.

---

