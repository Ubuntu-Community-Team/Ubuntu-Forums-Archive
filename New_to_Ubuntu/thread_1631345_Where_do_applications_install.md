---
title: "Where do applications install??"
date: 2010-11-26
forum: New to Ubuntu
---

### Post by phoenix17 on 2010-11-26
Just a quick question, but I couldn't really find a full answer from searching.

Where do applications install? When I installed ubuntu, I gave the "/" partition (root, right???) I gave that 4Gb.
Swap=2Gb (RAM=4Gb)
/home=remaining 170 some Gb.

I thought applications would install in the giant empty /home file, but it was telling me I was out of room. So I booted from a USB, ran GParted, reduced my Swap to 2Gb, and added that 2GB to the "/".


So where do applications install? Should I resize some stuff and give the "/" like 20-40 GB just to be safe? Because having to move the files all later sounds risky. I already messed it up once and had to wipe and reinstall... Pain in the you know what :p

---

### Post by mikewhatever on 2010-11-26
Most applications are installed into /usr. 10-20GB is a good size for the root partition.

---

### Post by chamira on 2010-11-26
I think most applications install in the /usr sub-directory so yes you need to give the main root some space 4Gb isn't going to be enough - most people suggest around 30-40Gb.

---

### Post by karthick87 on 2010-11-26
Generally user applications will be installed in **/opt**

---

### Post by phoenix17 on 2010-11-26
My hard drive is listed 640, but about 420 of that is still Windows (I only recently added Ubuntu). I can afford quite a bit of space for it, but I don't want to waste any space. Would 20 be good do you think for a long time of installing stuff?

And to resize it, would you shrink the /home, move the Swap, then extend the "/"?

Is "/" what they refer to as the ".root" file? I only saw someone write "make the / file at least 4 Gb".

Thanks for all the help!

---

### Post by SeijiSensei on 2010-11-26
Pretty much everything you install from repositories will be installed in /usr/bin or /usr/sbin.  The latter is used for things like server "daemons" where access is generally limited to the administrator.  /usr/bin holds software usable by ordinary users.

There is also a /bin and a /sbin directory.  These contain programs that are required by the system during the initial boot.  It's possible to place /usr on a separate partition; it will only be mounted when the system switches from single-user to multi-user mode during startup.  So /bin contains binaries like mount that the operating system needs before going multi-user.

> **karthick87 said:**
> Generally user applications will be installed in **/opt**

That's generally not true for most custom software compiled for Linux.  In most cases if you're building from source, the results are stored in the /usr/local branch with binaries in /usr/local/bin, libraries in the /usr/local/lib, and configuration file in /usr/local/etc.

/opt tends to be used by packages created for other Linux flavors like Solaris and some of the BSD derivatives, I believe.  I'll still see the occasional Linux package install itself to /opt, but they are very rare in the Linux world.

---

### Post by chamira on 2010-11-26
> **karthick87 said:**
> Generally user applications will be installed in **/opt**

Isn't /opt for commercial software and /usr for software downloaded through the software manager?

Regardless, everything ios loaded on to sub-directories of root so it needs space.

---

### Post by philinux on 2010-11-26
See this for where linux puts things. I've always set / up with 12gig and never run into any issues.
Home only contains application config files which are usually quite small.
Exceptions being browser and email.

The only thing in my /opt is adobe reader.

---

### Post by ezsit on 2010-11-26
Do not forget that /tmp and /var need space for working room for files used by programs in use and log files. If you plan to burn DVDs, leave at least 8 GB free so /tmp can grow and shrink. I'd suggest 30GB for /  You have plenty of space, why worry?

---

### Post by phoenix17 on 2010-11-26
> **ezsit said:**
> Do not forget that /tmp and /var need space for working room for files used by programs in use and log files. If you plan to burn DVDs, leave at least 8 GB free so /tmp can grow and shrink. I'd suggest 30GB for /  You have plenty of space, why worry?


Yeah that's how I feel. If I got the space and I can afford to use it, I want to give it about +30% of the largest I think it will need for the "why worry" thing, as you say. If it eliminates one headache of resizing later, I've saved time, minimized risk, and it is worth it to me.

I'll give this until tonight for more inputs and previous learning experiences. I hate being a needy guy on forums :(   But hopefully soon I will be able to help people like I'm being helped. I have no problem paying it back lol, but for the time being, I'm still on my learning curve.

I really appreciate all the help!

---

