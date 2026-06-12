---
title: "How can I import my ~/.ssh/ files to a new computer?"
date: 2018-09-24
forum: Networking &amp; Wireless
---

### Post by Vijit_Singh on 2018-09-24
Hi,

My laptop with the original .ssh/ folder ( including id_rsa, id_rsa.pub, known_host ) crashed. So I re installed Ubuntu on a new hard drive with the same user name and host name. I imported to ~/.ssh/..., However I cannot ssh to my servers like how I was able to before. I have turned off password authentication on my server so I am locked out if I cannot import these keys.

Thanks

---

### Post by TheFu on 2018-09-24
Perhaps a permissions issue?  ssh is picky about permissions.

[https://askubuntu.com/questions/134975/copy-ssh-private-keys-to-another-computer](https://askubuntu.com/questions/134975/copy-ssh-private-keys-to-another-computer)

---

### Post by Vijit_Singh on 2018-09-25
Thanks for the help! I don't know how I couldn't find that link in my search. 

The solution that worked for me was: 

 Try running ssh-add before you SSH into the server - you should then be prompted for the password and then subsequent ssh connects can use your private key.
  The ssh-add command adds the keys to the key agent.

---

### Post by TheFu on 2018-09-25
> **Vijit_Singh said:**
> Thanks for the help! I don't know how I couldn't find that link in my search. 

Don't use Bing to search for Linux stuff. ;)

> **Vijit_Singh said:**
> 
The solution that worked for me was: 

 Try running ssh-add before you SSH into the server - you should then be prompted for the password and then subsequent ssh connects can use your private key.
  The ssh-add command adds the keys to the key agent.

I've never used ssh-add in my life.  I've moved ~/.ssh/ stuff full of private and public keys multiple times between multiple computers (usually laptop --> laptop --> laptop) from backups.  I also run ssh-agent at GUI login on my desktop systems, but that is unrelated really.  If you have a DE on an ubuntu desktop, it should do this automatically.  I don't use DEs.

Lastly, thanks for say what did solve the issue.  If you could please mark this thread as SOLVED (Thread tools button near top), that helps the entire community.

---

