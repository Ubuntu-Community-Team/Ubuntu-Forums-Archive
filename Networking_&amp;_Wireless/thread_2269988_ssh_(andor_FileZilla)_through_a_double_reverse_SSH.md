---
title: "ssh (and/or FileZilla) through a double reverse SSH tunnel"
date: 2015-03-19
forum: Networking &amp; Wireless
---

### Post by Pj1989 on 2015-03-19
I have 3 PCs: 
[LIST]
[*]hostA is behind a firewall and cannot be reached from outside the local network
[*]hostB is outside the hostA network, has a public DNS but cannot see hostA
[*]hostC is a laptop without public DNS that often changes IP
[/LIST]

I would like to create a reverse ssh tunnel from hostA to hostB in order to allow hostC to reach hostA passing through hostB. I read some guides and followed the procedure, but i'm doing something wrong.

I try to recap what've done.
Doing this on hostA
```
userA@hostA :$ ssh -Nfg -R 2210:localhost:22 userB@hostB
```
allows me to reach hostA from hostB doing
```
userB@hostB :$ ssh -p 2210 userA@localhost
```
To reach hostA from hostC I can do on hostC
```
userC@hostC :$ ssh userB@hostB
userB@hostB :$ssh -p 2210 userA@localhost
```
Until now everything looks great. Now I would like to connect from hostC to hostA directly. This is not laziness, but is (i think) required to use FileZilla from hostC to hostA.


I go back to step 1 and do on hostA:
```
userA@hostA :$ ssh -Nfg -R :2210:logalhost:22 userB@hostB
```
note the ":" before 2210

I also edited the /etc/ssh/sshd_config file on hostB adding at the end.
```
GatewayPorts yes
```
But doing on hostC
```
userC@hostC :$ssh -p 2210 userA@hostB
```
returns a timeout error. Question 1) Is userA@hostB correct? If I understood correctly I have to tell ssh to connect to the port 2210 of hostB, that port however should be forwarder to hostA that would ask for userA credential. Is this true?

Question 2) Where I do wrong?
Thank you very much

PS: also another way to open the tunnel and allow FileZilla to connect from hostC to hostA would be ok.

---

### Post by Lars Noodén on 2015-03-19
> **Pj1989 said:**
> 
I try to recap what've done.
Doing this on hostA
```
userA@hostA :$ ssh -Nfg -R 2210:localhost:22 userB@hostB
```
allows me to reach hostA from hostB doing...

You have created a reverse tunnel from port 22 on A to port 2210 on B.  
Add a regular tunnel from any port on C (e.g. 2212) to port 2210 on B.

```

ssh -L 2212:localhost:2210 userB@hostB

```

Then on C you can point FileZIlla, or any other SFTP client, at port 2212 on the localhost and it will be connecting to A. 

That's one way to do it.

If you set up a dynamic DNS account somewhere for C, then another option opens up.

---

### Post by Lars Noodén on 2015-03-19
Also, you can keep "GatewayPorts" set to "no" on host B and the others.  That is the default, anyway.

---

### Post by Pj1989 on 2015-03-19
Your solution looks great.

Unfortunately A is a computer cluster and tonight there was a power interruption, so I will test it tommorow.
I'll let you know asap!

Thank you soooo much.

---

### Post by Lars Noodén on 2015-03-19
Once you have checked that the above works, you can automate the connection using a single-purpose key. 

If you make a key on A just for the reverse tunnel, when you put it on B you can restrict it with a forced command such as /bin/false

```
**command="/bin/false"** ecdsa-sha2-nistp256 AAAAE2VjZHNhLXNoYTItbmlzdHAyNTYAAAAIbmlzdHAyNTYAAABBBNnRcd4u0uAXeMm6j6Viv+NuJ0J5eyqbNm6AkBWSGjkVxky0WrOHtnsLS7QQfDe5v9CFZhC9Fu1XfSIvw1wrN4w= hosta tunnel

```

That prevents it from being used for anything else.  Then you can have a cron job on host A try making the tunnel by running ssh repeatedly.

```

ssh **-o ExitOnForwardFailure=yes** -R 2210:localhost:22 -Nf -i /home/pj1989/.ssh/key_hostb userb@hostb

```

The -R, -N, and -f you know about and the -i points ssh at the specific key to be used.  The important part is the -o to set one configuration option.  The -o [ExitOnForwardFailure](http://manpages.ubuntu.com/manpages/trusty/en/man5/ssh_config.5.html) causes ssh to quit if there is already a tunnel in place.  If there is no tunnel, then it sets one up.  That save having to make a fancier way of checking if the tunnel is still up.  The downside is that it prints an error if there is already a tunnel, but that can be zapped by redirecting stderr to /dev/null if you like.

---

### Post by papibe on 2015-03-19
Hi Pj1989.

Does any of these connections would go over the Internet? If so, you may consider tunning a couple of ssh options.

IMHO, it takes too much time for ssh to to realize it has actually died. That is, the time between your data transfer stall, because something went wrong with the connection, up until the time the tunnel/ssh connection actually timeouts and exit.

So in my experience, if your connection is setup for data transfer, it works better with tighter timeouts. I have better results by forcing the connection to die faster, creating another connection, and then continuing the transfer, than waiting several minutes while it stalls. This works great when using rsync with the --partial option as you never have to star over the transfer of a file that was 'interrupted' (see post #2 [here]("http://ubuntuforums.org/showthread.php?t=1861143&highlight=partial")).

What I do is disable the TCP default timeouts, and make ssh itself take notice of the timeouts:
```
ssh -o TCPKeepAlive=no -o ServerAliveInterval=40  ...
```
Just a thought. Hope it helps.
Regards.

---

### Post by Pj1989 on 2015-03-30
First of all, excuse me if it took me a long time to reply.

**The Lars method worked like a charm!** I can easily set up the connection and use it both for access a remote terminal and to trasfer files using a GUI program like FileZilla. This is extremely helpfull for me. Thank you very much. :grin:

> **Lars Noodén said:**
> 
Once you have checked that the above works, you can automate the connection using a single-purpose key. 

If you make a key on A just for the reverse tunnel, when you put it on B you can restrict it with a forced command such as /bin/false

```
**command="/bin/false"** ecdsa-sha2-nistp256 AAAAE2VjZHNhLXNoYTItbmlzdHAyNTYAAAAIbmlzdHAyNTYAAABBBNnRcd4u0uAXeMm6j6Viv+NuJ0J5eyqbNm6AkBWSGjkVxky0WrOHtnsLS7QQfDe5v9CFZhC9Fu1XfSIvw1wrN4w= hosta tunnel

```

That prevents it from being used for anything else.  Then you can have a cron job on host A try making the tunnel by running ssh repeatedly.


Ok. I'm sorry but I didn't understand. An option to be sure noone else  use this connection is of course welcome. Are you talking about  ssh-keys? Where should i put the "command" line you suggested and what is that long string of character?

> **Lars Noodén said:**
> 
```

ssh **-o ExitOnForwardFailure=yes** -R 2210:localhost:22 -Nf -i /home/pj1989/.ssh/key_hostb userb@hostb

```

The -R, -N, and -f you know about and the -i points ssh at the specific key to be used.  The important part is the -o to set one configuration option.  The -o [ExitOnForwardFailure]("http://manpages.ubuntu.com/manpages/trusty/en/man5/ssh_config.5.html") causes ssh to quit if there is already a tunnel in place.  If there is no tunnel, then it sets one up.  That save having to make a fancier way of checking if the tunnel is still up.  The downside is that it prints an error if there is already a tunnel, but that can be zapped by redirecting stderr to /dev/null if you like.


 Is this related to the creation of a crontab comman to be executed periodically on A? Otherwise isn't  ```
ps -ef | grep ssh 
``` enough to see if the tunnel is still open? Anyway A is a computation cluster that is turned on 24/7, so I hope to tunnel to be pretty stable.

> **papibe said:**
> Hi Pj1989.

Does any of these connections would go over the Internet? If so, you may consider tunning a couple of ssh options.

IMHO, it takes too much time for ssh to to realize it has actually died. That is, the time between your data transfer stall, because something went wrong with the connection, up until the time the tunnel/ssh connection actually timeouts and exit.

So in my experience, if your connection is setup for data transfer, it works better with tighter timeouts. I have better results by forcing the connection to die faster, creating another connection, and then continuing the transfer, than waiting several minutes while it stalls. This works great when using rsync with the --partial option as you never have to star over the transfer of a file that was 'interrupted' (see post #2 [here]("http://ubuntuforums.org/showthread.php?t=1861143&highlight=partial")).

What I do is disable the TCP default timeouts, and make ssh itself take notice of the timeouts:
```
ssh -o TCPKeepAlive=no -o ServerAliveInterval=40  ...
```
Just a thought. Hope it helps.
Regards.

Actually B is on the internet, so yes: both the connections A <- B and C -> B are on the internet. I will try your solution and see if it's helpfull. Thank you very much for the tip ):P

---

