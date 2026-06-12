---
title: "VLC Home Server Simple Question"
date: 2008-06-10
forum: Networking &amp; Wireless
---

### Post by helixed on 2008-06-10
Hello everybody,

I would like to set up a home server using vlc.  Mostly this server will be contained with my home network, but occasionally it would be nice to be able to access files outside of my network.  I've been trying to figure out which protocols to use and how it should be set up.  I already have an ftp server set up, but I think for my purposes it won't be enough.  My main wants are:

[LIST=1]
[*]Security - I want the stream to be encrypted with something like ssh so that if anybody else is on the network they can't see what I'm doing (the networks may be public).
[*]Easy Access - I'm willing to take as much time to set this up as needed, but once I do I don't want it to be too difficult to open a movie file.  
[*]use of Multiple File Formats - My video collection came from a variety of different sources.  Some of the container formats include mkv's and avi's, with a variety of different codecs including divx, mkv, xvids, etc.  If possible I would like to not have to transcode the files, simply because it eats up processing power I use for other things on the server.  
[/LIST]

I don't know if what I want to do is possible, but if anybody could help me I would really appreciate it.  I don't need an entire guide or anything, just which protocols to use and maybe a link or two would be nice.

Thanks,

helixed

---

### Post by nixscripter on 2008-06-11
I haven't used VLC, but I can certainly help you with step 1.

SSH allows you to set up a tunnel. It's somewhat awkward, but this is one way you can do it.

Suppose the server is machine A running the VLC server on port 9876 (not sure what it acually is), and the machine you want to view the file on is machine B.

On machine B, run this command: ```
ssh -L 1234:machinea:9876 machinea
``` This will let you log into machine A with your account, and give you a shell if it has sshd running (and port forwarding allowed, which is on by default). Keep this shell open; if it gets annoying, ssh has commands to hide and background the job (see the the man page).

Then have your client connect to localhost port 1234. What happens is the data is forwarded over the ssh connection to the other server on port 9876, which allows for the data transfer.

As I said, it's somewhat awkward, but this is how I do my e-mail for example. Hope this helps.

---

### Post by helixed on 2008-06-11
Thanks for the quick reply.  That works great.  Is there any way to test if an ssh connection is working (I'm a little paranoid)?  Also, how can I tell which port the service is using?

Thanks,

helixed

---

### Post by nixscripter on 2008-06-13
I'm not quite sure what your question means.

In my above example there are two TCP connections:

```

       port ??     port 1234
program  --------------> ssh
       port ??     port 9876
ssh      --------------> server-sshd

```

The two ports on the sending ends are dynamically selected by the system when the socket is created.

If all you meant "what port does VLC use", according to skimming the docs, it's user configurable. If you don't know, just have the server running, and try this command to list connections: ```
netstat --ip --listening
``` It should be in the list.

SSH can be detected with the same command. From the client end, just don't use "--listening".

Hope this helps.

---

