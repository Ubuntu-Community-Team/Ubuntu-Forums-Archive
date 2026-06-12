---
title: "Network problems"
date: 2011-04-08
forum: New to Ubuntu
---

### Post by sandy0594 on 2011-04-08
I installed **ubuntu 10.10** desktop edition 4 days back..after that i tried very hard to configure n/w connections as i am new to linux..I updated the packages using synaptec package manager..When it asked for restart,i did it.But after ***reboot*** i was shocked to see my **Internet stopped working**..i had to configure everything again..can anyone say why this happened?

---

### Post by jtarin on 2011-04-09
The updating of some software possibly overwrote older configuration files.

---

### Post by sandy0594 on 2011-04-09
Why is it like that? is there no safety for what we have configured.If everything happens on it's own how an we control the settings..I had to try hard for configure n/w connections and now it just went like that

---

### Post by jtarin on 2011-04-09
Rather than "why is that" why not "I will discipline myself to make a note of applications being updated and attempt to backup configuration files for said applications before I let them be overwritten". Linux teaches us to be more responsible for our actions, so we can be, if we so choose, completely aware of what is going on with our system. Of course it's a lot less work sometimes just to reconfigure something.....than all that backup. Things do not happen on their own. :)

---

### Post by sandy0594 on 2011-04-09
But,the packages which got installed has nothing to do with the packages which are used for n/w connections..For me,i had to install **AR81Family-linux-v1-1.0.1.14.patch.tar.gz **and **AR81Family-linux-v1.0.1.14.tar.gz**..After installing these 2 packages along with package **patch** i am done configuring my n/w connections..As per my knowledge the 3 packages which i said above didn't get updated.So,where is the point that they might be overriden?

---

### Post by jtarin on 2011-04-09
Your network configuration is dependent on more than just those three packages. I could not begin to tell you what in your update changed your configuration without a list of what you updated. Suffice to say you located your problem and remedied it. Same process in Windows when you lose a connection because of some reconfiguration. Those packages you  mention above are not standard Ubuntu packages so therefore there is no guarantee that your configuration will work exactly as intended from time to time. You might have to adjust this after every kernel update as this module was not included in the Linux kernel, but might be in future ones..

---

### Post by sandy0594 on 2011-04-09
So,compromising is the best thing to do..Anyhow,thanks for the reply j

---

### Post by gandaran on 2011-04-09
> **sandy0594 said:**
> But,the packages which got installed has nothing to do with the packages which are used for n/w connections..For me,i had to install **AR81Family-linux-v1-1.0.1.14.patch.tar.gz **and **AR81Family-linux-v1.0.1.14.tar.gz**..After installing these 2 packages along with package **patch** i am done configuring my n/w connections..As per my knowledge the 3 packages which i said above didn't get updated.So,where is the point that they might be overriden?you will have to reinstall those drivers every time there is a kernel update until one day the new kernel will have the same drivers included then they will work.

---

### Post by sandy0594 on 2011-04-09
Thanks for ur people time

---

