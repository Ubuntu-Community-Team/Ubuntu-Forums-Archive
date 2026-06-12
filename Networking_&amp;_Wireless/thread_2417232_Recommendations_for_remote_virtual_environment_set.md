---
title: "Recommendations for remote virtual environment setup"
date: 2019-04-22
forum: Networking &amp; Wireless
---

### Post by beefsteaktom on 2019-04-22
Hi all,

I'm wanting to create a solution that will allow me to execute data science / machine learning workflows on my home system (Ubuntu Desktop) from my laptop  (Ubuntu Desktop) remotely whilst connecting outside of my LAN; 

Further more I would like to interface with the system via a GUI, mimicking the full desktop UX as much as possible, rather than a SSH shell session.




I have played with the Screen Share functionality on Ubuntu but I don't know if this is the best solution. 

Could you recommend a solution for myself to look into? I'm relatively new to Linux, so any advice big or small would be appreciated... 

Thanks BST

---

### Post by TheFu on 2019-04-22
Use ssh for 95% of these things.
Use x2go for the remaining 5%.

x2go feels 2-3x faster than all the other options.  x2go is based on the NX protocol and uses ssh authentication. It doesn't need any other ports open.  ssh-keys work, so you should only allow key-based authentication from internet IPs and setup fail2ban to block brute force attacks.  x2go honors the ~/.ssh/config file, so using alternate ports, different logins and short-names for the connection are possible.

I'm assuming you have ssh working externally already, have a DNS record for the public IP too.

I don't know what you mean by "screen share" - all remote desktop solutions run their own X/Session, so it won't show what is already on the physical machine at home, but it will create a virtual screen.  You'll see.  I run my main desktop inside a virtual machine and access it from multiple client systems local and remote.

---

### Post by slickymaster on 2019-04-22
Thread moved to **Networking & Wireless** for a better fit

---

