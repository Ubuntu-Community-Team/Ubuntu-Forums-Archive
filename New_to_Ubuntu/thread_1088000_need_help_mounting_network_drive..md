---
title: "need help mounting network drive."
date: 2009-03-05
forum: New to Ubuntu
---

### Post by rgb96 on 2009-03-05
Hi all, 


I need to mount a network drive that is available to everyone in our company to this linux machine so I can access it. When you log into windows from any computer, it is just one of the options under my computer.

I tried following a tutorial, but I can't figure out what to name it in fstab. I tried all the names that made any sense, and I don't know the ip, or how to get the ip, or if there is an ip. Can some one point me in the right direction?

---

### Post by kanikilu on 2009-03-05
I use Places > Connect to Server > Service type: Windows share.

As for the other information, you'll need to get that from someone there. You need the server name or IP address at the very least.

Can you walk over and see it on a Windows computer? You can get the server and share name from there...

---

### Post by rgb96 on 2009-03-05
Yeah. I can get on a windows comp. How do I access the share name once I do?

---

### Post by kanikilu on 2009-03-05
Open up a command window: Start -> Run (if on XP) -> type **cmd** and press enter. At the command prompt, type **net use** and press enter. Copy and paste (or write down and type) the output here if you can. What you're looking for is the remote path (will look like "\\server\share") that corresponds with the drive letter you wish to access.

---

### Post by rgb96 on 2009-03-05
Okay, tried that but it didn't work. The line I put into fstab was this:

```
//srv-app1/NETDATA /media/NetworkDrive smbfs guest 0 0
```

and the error message I got was this

```
Warning: mapping 'guest' to 'guest,sec=none'
mount error: could not find target server. TCP name srv-app1/NETDATA not found
No ip address specified and hostname not found

```

---

### Post by kanikilu on 2009-03-05
What about "net use" on Windows didn't work? It wouldn't help if you could elaborate a bit...

Try pinging serv-app1 from ubuntu to get it's IP address:

```
ping -c 3 srv-app1
```

You may need a fully-qualified domain name, though, like "srv-app1.domain.com", but the domain would be specific to your network, so I can't tell you what that is...

Also, I would personally try to connect using the method I described earlier (Places > Connect to server) to see if you can even get that to work before messing with fstab.

---

### Post by rgb96 on 2009-03-05
Well, you were right about the specific domain name, so I used that to get the ip, but when I put that into places->connect to server, I got an error. This one specifically:

"volume doesn't implement mount"

---

### Post by kanikilu on 2009-03-05
I haven't seen that error before...is this network share encrypted by any chance?

---

### Post by rgb96 on 2009-03-05
how can I know?

---

