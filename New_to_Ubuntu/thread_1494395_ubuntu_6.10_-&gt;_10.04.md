---
title: "ubuntu 6.10 -&gt; 10.04"
date: 2010-05-26
forum: New to Ubuntu
---

### Post by aGit on 2010-05-26
Hey,

I recently dug up my trusty old via itx-nano and noticed it still had my age old unbuntu 6.10 install in it. Which was fine since i would have installed linux on it anyway. Now the problem is, the ubuntu is so old that the repositories do not work anymore, so i'm having hard time installing any updates, or any programs what so ever.

I tried adding a few new repos through synaptic package manager, but to no avail. i gept geting the same old 404 errors on apt-get update. In effect, nothing works.

[http://www.notafront.org/~agit/404.jpg](http://www.notafront.org/~agit/404.jpg)

Due to this same problem, i cannot just simply update to 7.10 from the update manager, as i get the error "Could not find the release notes - the server maybe overloaded" I'm sure the overloaded part in this case means, "non existant"

The itx has no usb-boot cababilities, and for some reason or another, probs due to the usb->ps/2 adapter failing, i cannot access bios to set boot order to start from cd. So a fresh install from the cd-image i downloaded is out of the question.

the latest thing i tried was apt-get dist-upgrade which supprisingly worked  
well enough, but after having downloaded 666mbs of updates i got the
E: Couldn't configure pre-depend libc6 for findutils, probably a dependency cycle. and tbh, i have no clue what so ever what this is about, or how to redeem the situation.

So to cap it up, i'm at lose here, repositories doesnt work, cant find ones with distro upgrades that fit the age-old 6.10, fresh install from cd doesnt work. usb-stick install doesnt work.

sorry for the wall of text, i just cant explain anything without an essay.



-agit

---

### Post by aGit on 2010-05-26
i managed to breath some life into the system by following the advice at [http://ubuntuguide.org/wiki/Ubuntu:Edgy/Repositories](http://ubuntuguide.org/wiki/Ubuntu:Edgy/Repositories) and doing apt-get update i'm not completely sure what this does, as i still got a whooole lot of 404s from non-working repos, but some of them has to still work as something got downloaded. Huge majority of the packages didnt tho.

edit:

Reading package lists... Error!
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
E: Dynamic MMap ran out of room
E: Error occurred while processing toilet (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/fi.archive.ubuntu.com_ubuntu_dists_feisty_universe_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
agit@Simulacrum:~$ 


=(

---

### Post by -humanaut- on 2010-05-26
I honestly don't think it's going to be possible to upgrade all the way to 10.04 from 6.10 Clean install is going to be your only option.

---

### Post by Mark Phelps on 2010-05-27
You're not going to be able to leap from 6x to 10x in one jump, and doing incremental upgrades is going to present lots of problems along the way.

The only real way to do what you want is to clean-install 10.04 -- after saving off your data and files.

---

