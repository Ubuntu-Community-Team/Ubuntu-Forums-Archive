---
title: "Newbie SSH question."
date: 2007-03-22
forum: Networking &amp; Wireless
---

### Post by whitefort on 2007-03-22
Hi,

I have 3 Ubuntu machines on a network.  I've set up the SSH daemon on one of them  ('mars').  When I go to another machine on the network, open a terminal, and type **'ssh mars**',  (as in the example in my book) it doesn't work.  However, when I type its full address - 'ssh** 193.168.0.5'** - it works perfectly.

Of course, the same thing happens when I try to ping any of the machines.

I'd be grateful if anyone would tell me what I need to do so that I can ssh 'machine_name', rather than 'ssh full_address'.

Also, as a secondary question, once I make the connection, is there any way I can use a GUI ?  What I'd really like to do is to be able to do is transfer files from one machine to another using a 'drag and drop' interface.

Or am I hopelessly confused, and should be using something else instead of SSH?

I'd really appreciate any help!  Thanks.

---

### Post by tribaal on 2007-03-22
The cleanest linux way of doing this (resolving by hostname rather than by IP) would probably to simply add the following line to your /etc/hosts file:

193.168.0.5 Mars

Save and close.
Now you should be able to "ssh Mars"  with no problems :)

The windows way would be to use the WINS package (this is the protocol that helps windows machines figure each other's hostname on a network (to make it short).

Hope this was the kind of answer you were looking for :)

- trib'

---

### Post by mbeierl on 2007-03-22
ssh is for remote console level logins.  What you really want is a network file system so that you can access the other computer as a directory on the local comptuer.  Try nfs.

---

### Post by chili555 on 2007-03-22
How does your computer know mars' number? It looks in /etc/hosts (no help here) and may look at the DNS servers (no help here, either). So let's build a little directory in /etc/hosts. sudo gedit /etc/hosts to add something like:```
192.168.0.5  mars
192.168.0.6  venus
192.168.0.7  earth
```

ssh wants the user name, so you will be able to```
ssh chili@mars
```

When I want to drag-n-drop, I go to Places -> Connect to server and select ssh. I fill in the server name, mars, in your example, and a user name and click Connect. Then I have a folder on a wire, a network share, on my desktop. When I right-click to browse this, I am prompted for the user's password and I can browse and drag-n-drop to my own /home folder.

Post back if you need more.

PS - for lurkers: this works perfectly on **all linux** systems. If you so-last-century still have Windows, you need Samba.

---

### Post by whitefort on 2007-03-22
Many thanks, guys.

As a recent convert, I still break into a sweat at the thought of going in and changing config files manually - I'm always convinced that if I do this, the next time I reboot, my PC  will burst into flames, my house will fall down, the Stock Market will collapse, and my cat will get sick.

But this was easy and painless, and it's working perfectly now.  Many thanks!

My next project is to look at nfs.

Thanks again!!

---

