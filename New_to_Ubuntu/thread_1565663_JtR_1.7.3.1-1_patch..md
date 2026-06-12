---
title: "JtR 1.7.3.1-1 patch."
date: 2010-09-01
forum: New to Ubuntu
---

### Post by newport_j on 2010-09-01
I have john-the-ripper 1.7.3.1-1 on my Ubuntu 10.04 computer. is there a patch for this as there are patches for other versions of JtR? I run it on an MD5 password (it says MD5 when I use JtR to attempt to crack it) and while it runs, it does take a long time to crack the password. I have yet to reach the end when the password is actually cracked.
 
The question agan is: is the a patch for JtR 1.7.3.1-1? If there is where can I download it?
 
Newport_j

---

### Post by Rubi1200 on 2010-09-01
This is not your first post on this subject (at least the third or fourth now I think) and I have to ask this: Why?

With all due respect, you seem to be running in circles a little with this and unless you have highly sensitive data you are trying to protect why are you going to all this trouble?

I have a 16 character password and am reasonably confident that it is "safe." I do not feel the need to try and crack it to see if it is secure.

Even if you do crack your password, what then? A new password, more cracking attempts?

If you follow the advice in the security stickies by bodhi.zazen you will find that your setup is pretty secure.

As I said, I mean no disrespect and I wish you the best of luck in your endeavors.

---

### Post by dynamo2 on 2010-09-01
If there is a patch (I dont know exactly which kind of patch your asking for), you need to patch the source code, you cant just install from the Ubuntu repos and hope to somehow patch that. Please, check out [http://www.openwall.com/john/](http://www.openwall.com/john/) its the official page, and tells how to patch (also includes patches).

---

### Post by newport_j on 2010-09-01
John the ripper would be a fine pwd cracker. But it takes a long time to crack. I have run it for days and it is churning, but no output. Thta is why I switched to Ophcrack. 
 
I think if I buy wordlists then JtR will crack faster (I do not see how it can be any slower), but that is the catch. I have to buy wordlists. So I just use the brute force method and hope for the best. 
 
I have let it run from Sunday night to Thursday afternoon and then I stopped it. It seems the cracking time it too long. I would just like to see it crack. 
 
That is why I jumped to Opchrack. I was lookng for something faster. Someone here recommended it.
 
I am using john 1.7.3.1-1 and it seems thta these files collections always have a new patch that reflect additonal algorithms recently discovered and verified for a new pwd encryption. I was just wondering where the latest path is for john 1.7.3.1-1.
 
Newport_j

---

### Post by nixor01 on 2011-05-08
In case anyone is still wondering. I use 'sudo apt-get install john' and it came with version 1.7.3
which doesn't support certain functionalities, resulting in 'No password hashes loaded'

However if you download the latest john source code now and compile it, you get the ver 1.7.7, then it works like a charm.

---

