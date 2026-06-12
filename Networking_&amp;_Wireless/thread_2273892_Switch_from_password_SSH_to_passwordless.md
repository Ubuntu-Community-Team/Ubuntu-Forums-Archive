---
title: "Switch from password SSH to passwordless"
date: 2015-04-16
forum: Networking &amp; Wireless
---

### Post by ray field on 2015-04-16
I mostly use SSH to sync with my desktop using Unison, but would also like to switch to SSH tunneling when I'm out of my office. I set up my netbook (Acer C720 with Crouton w/128GB HD swapped in, great little machine) to use SSH with a password -- without really realizing how insecure it was.

Now I want to change it to passwordless for obvious reasons. I tried to do it the other way but managed to munge things up so badly, I had to restore my netbook's prior SSH settings. Can someone suggest a step-by-step?

---

### Post by TheFu on 2015-04-16
Yes, using passwords is a failure.

[http://blog.jdpfu.com/2011/07/14/easy-key-based-ssh-authentication](http://blog.jdpfu.com/2011/07/14/easy-key-based-ssh-authentication) ... there's a URL there (not a link, sorry). I provide this one, since it goes into other things for after you have ssh-keygen run.

I have a C720 too - no crouton - 100% ubuntu server + openbox/WM install.  Love it, except the touchpad driver and DOG NMAD FRAKING power key where the DEL key belongs.

Oh - and after you get ssh working ... read this [http://blog.jdpfu.com/2014/09/23/you-don-t-know-ssh-about-ssh](http://blog.jdpfu.com/2014/09/23/you-don-t-know-ssh-about-ssh) to see a few of the other tricks having ssh unlocks. I think you'll be surprised.

---

### Post by ray field on 2015-04-16
thanks, that was easy enough, I really can't remember how I was trying to make it difficult

next I edited my desktop's /etc/ssh/sshd_config and uncommented

# PasswordAuthentication yes

and changed the value to "no"

thanks --

---

### Post by TheFu on 2015-04-16
Only the server-side setting for sshd_config matters, not the client.

---

