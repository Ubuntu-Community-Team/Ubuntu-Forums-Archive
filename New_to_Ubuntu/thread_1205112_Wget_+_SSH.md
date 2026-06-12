---
title: "Wget + SSH"
date: 2009-07-05
forum: New to Ubuntu
---

### Post by pi.boy.travis on 2009-07-05
OK, I have a file server with SSH.  Lets say that I have this huge file I want to download from the Internet.  Could I SSH to the server, pass the link to Wget, then disconnect, leaving Wget to do the work?  How can I go about letting Wget run autonomously even though I'm no longer logged in via SSH?

Thanks in advance!

---

### Post by rampageoberon on 2009-07-05
Hi there,

I don't think you can carry on a download over ssh if you terminate the session.

If you can download the fle to the server you can always get it using sftp, otherwise i tend to use http using an ssh tunnel.

Hope that helps

---

### Post by DavePlummer on 2009-07-05
I do that frequently using the screen command:

```
screen wget http://some.url/
```

Then press CTRL+a, and then "d" to detach the screen. Wget will continue to run even after you close the ssh session.

---

### Post by scrooge_74 on 2009-07-05
What about using the scp command?

---

### Post by scorp123 on 2009-07-05
> **pi.boy.travis said:**
> OK, I have a file server with SSH.  Lets say that I have this huge file I want to download from the Internet.  Could I SSH to the server, pass the link to Wget, then disconnect, leaving Wget to do the work?  How can I go about letting Wget run autonomously even though I'm no longer logged in via SSH? ```
sudo apt-get install screen screen-profiles
```

Launch "screen" inside your SSH session. Do whatever you need to do, e.g. get "wget" going. When you want to leave, hit "CTRL+A", and then "D". The session will be detached (use "screen -r" or "screen -x" to re-attach again).

More detailed tutorials:
[http://www.linuxjournal.com/article/6340](http://www.linuxjournal.com/article/6340)
[http://www.kuro5hin.org/story/2004/3/9/16838/14935](http://www.kuro5hin.org/story/2004/3/9/16838/14935)

---

### Post by scorp123 on 2009-07-05
> **scrooge_74 said:**
> What about using the scp command? And that is going to help him ... how? He wants to log in from work into his machine at home and he wants his machine at home to download a few files in his absence ... So how exactly is "scp" going to solve that problem, especially if he has to disconnect the session because he can't leave it open?

---

### Post by scrooge_74 on 2009-07-05
> **scorp123 said:**
> And that is going to help him ... how? He wants to log in from work into his machine at home and he wants his machine at home to download a few files in his absence ... So how exactly is "scp" going to solve that problem, especially if he has to disconnect the session because he can't leave it open?

Oh my are we having a bad hair day?

He can ssh into his home machine and just use that command to get the file from where he wants to and just leave a little terminal window open somewhere in his desktop and let it be till it ends. Or from same ssh session just do wget and get the file from where ever it has to come.

Seems I can't find him saying the PC is at home and he wants to do some exact stuff.

---

### Post by pi.boy.travis on 2009-07-05
Excellent, screens seems to be doing the trick!  Thanks!

EDIT:YES!  I FINALLY GOT A COFFEE MUG!

---

### Post by scorp123 on 2009-07-05
> **scrooge_74 said:**
>  Oh my are we having a bad hair day? Nah. Just hinting at the possibility that "use scp" might not have been an helpful answer ;)

> **scrooge_74 said:**
>  He can ssh into his home machine and just use that command to get the file from where he wants to  Only if that remote location supports SSH connections ):P  ... Web servers usually don't, so you'd have to use "wget".

> **scrooge_74 said:**
>  and just leave a little terminal window open somewhere in his desktop and let it be till it ends. But sometimes exactly this isn't possible. What if your boss doesn't like the fact that you're connected all day long to a SSH server outside of the company? What if you have to move places, e.g. go to meetings, and thus place your laptop or whatever you are using into suspend? In such a case whatever program you were running on the remote end would die and the download would not finish.

> **scrooge_74 said:**
>  Or from same ssh session just do wget and get the file from where ever it has to come. That's the idea. But the point is: If you can't leave the session open (or you don't want to due to security reasons) then use "screen".

---

### Post by scrooge_74 on 2009-07-05
So with screen I can close the ssh session go to a meeting come back log back in and what ever I was doing with screen will still be running while I was away?

---

### Post by frunns on 2009-07-06
That's the idea. :) Just be sure to detach before logging out.

And I suppose you should be able to use nohup? Like this:
```
nohup <commmand> <args> &
```
Haven't tried that myself, but I suppose it should work...

---

### Post by scorp123 on 2009-07-06
> **scrooge_74 said:**
> So with screen I can close the ssh session go to a meeting come back log back in and what ever I was doing with screen will still be running while I was away? Exactly. That's the cool thing about screen. See my posting above. Even if the connection to your screen session gets abruptly terminated, whatever was running inside "screen" should continue to run. You just need to reconnect (e.g. "screen -x" or "screen -r" ...)

---

### Post by scorp123 on 2009-07-06
> **frunns said:**
> Just be sure to detach before logging out. "screen" should even survive unclean disconnects. I know this for fact. I once had a customer for whom I had to do remote support and those guys lived in the 1980's: instead of giving us SSH logins or VPN access they gave us analogue dial-up numbers .... ](*,)

Needless to say that this connection across a 1000 km long-distance call was anything but stable. But with "screen" at least whatever we were doing on their system would not end abruptly when the session dropped all of a sudden. We could just dial-in again and resume where we had left off.

Sometimes if you disconnect uncleanly from a "screen" session the reconnect command might refuse to work:
```
screen -r
``` ... Screen then complains "No detached sessions."

If that happens simply tell "screen" that you'd like a shared session with a non-detached session:
```
screen -x
``` ... And voila, you're back in, detached or not. The latter is also useful if multiple people should see the same thing. With "screen -x" you can share whatever is running inside there across multiple virtual terminals, be they SSH, telnet or console sesions. This too is a very useful feature.

---

### Post by frunns on 2009-07-06
I did not know that! But now that you mention it, it makes a whole lot of sense that it has that funcionality! Been a few years since I used screen...

---

### Post by pi.boy.travis on 2009-07-06
Actually, I just checked the Wget manpage, and you can pass the -b argument to get it to run in the background.  But then if you want to kill the download you have to remember the PID. . .

---

