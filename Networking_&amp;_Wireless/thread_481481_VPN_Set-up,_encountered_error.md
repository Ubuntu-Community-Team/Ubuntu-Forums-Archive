---
title: "VPN Set-up, encountered error"
date: 2007-06-22
forum: Networking &amp; Wireless
---

### Post by S15_88 on 2007-06-22
Hey there I'm new to linux and i'm learning it fairly fast and have grasped quite a few concepts so far and a co-worker who's knows alot about linux told me that a good project to learn from would be to set up a VPN.  I found a very straight forward guide [here]("http://builder.com.com/5100-6372_14-6038003.html") but i knew it was too good to be true.  I have encountered a problem at the first step.  i have all the files downloaded to a folder called VPN i switched to that directory and did 
> rpm --install dkms-1.12-2.noarch.rpm
and this is the output i got:
> 
alain@S15:~/Desktop/VPN$ rpm --install dkms-1.12-2.noarch.rpm
warning: dkms-1.12-2.noarch.rpm: Header V3 DSA signature: NOKEY, key ID b56a8bac
error: Failed dependencies:
        /bin/bash is needed by dkms-1.12-2.noarch
        /bin/sh is needed by dkms-1.12-2.noarch
        bash > 1.99 is needed by dkms-1.12-2.noarch
        cpio is needed by dkms-1.12-2.noarch
        findutils is needed by dkms-1.12-2.noarch
        gawk is needed by dkms-1.12-2.noarch
        grep is needed by dkms-1.12-2.noarch
        gzip is needed by dkms-1.12-2.noarch
        mktemp is needed by dkms-1.12-2.noarch
        sed is needed by dkms-1.12-2.noarch
        tar is needed by dkms-1.12-2.noarch
alain@S15:~/Desktop/VPN$ 


Just wondering what i should do now??  Any thoughts

Thanks, Alain

---

