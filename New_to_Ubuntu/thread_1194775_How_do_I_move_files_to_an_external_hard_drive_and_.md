---
title: "How do I move files to an external hard drive and then view them when I want"
date: 2009-06-23
forum: New to Ubuntu
---

### Post by mikodo on 2009-06-23
Hello everyone,

I would like to move files from my home folder (music, videos, pictures) to an external hard drive I used to use for backup in Vista and then view them in Ubuntu 8.04 when I please. I have no NTFS  files remaining, have wiped the external drive clean and hope that everything will be saved in the default ext3 format. I am sure there must be links for sites to learn these processes. I only use Hardy now.

Maybe the answer is to just drag them to the open hard drive.

Awaiting advice,

Mikodo

---

### Post by TheNad on 2009-06-23
I'm assuming it's attached via USB, correct? Anyway, once it's attached, it should just appear in Places > Computer (you might need a driver for the external drive but I doubt it). From there you should be able to navigate through anything you put on there and putting things on there should be equally simple. Just move items into it like any other place on your computer, either Save As or drag and drop should do it. Unless I missed something, it should be as simple as that. Good luck!

Afterthought: The drive should also appear on the desktop and under Places with a symbol all its own (as well as the location I mentioned above, Places > Computer).

EDIT: Not sure if it would make any difference, but to remove the drive properly you can "Unmount Volume" by right clicking on the icon for the drive on the desktop or any of the other locations I mentioned it would be.

---

### Post by mikodo on 2009-06-23
> **TheNad said:**
> I'm assuming it's attached via USB, correct? Anyway, once it's attached, it should just appear in Places > Computer (you might need a driver for the external drive but I doubt it). From there you should be able to navigate through anything you put on there and putting things on there should be equally simple. Just move items into it like any other place on your computer, either Save As or drag and drop should do it. Unless I missed something, it should be as simple as that. Good luck!

Afterthought: The drive should also appear on the desktop and under Places with a symbol all its own (as well as the location I mentioned above, Places > Computer).

EDIT: Not sure if it would make any difference, but to remove the drive properly you can "Unmount Volume" by right clicking on the icon for the drive on the desktop or any of the other locations I mentioned it would be.

Everything is as you assumed(USB), and works as you say! 

Thanks,

Mikodo

---

### Post by TheNad on 2009-06-23
> **mikodo said:**
> Everything is as you assumed(USB), and works as you say! 

Thanks,

Mikodo

Great!

---

### Post by Bucky Ball on 2009-06-23
Ubuntu reads/write to NTFS just fine. You could have left it as was. Go to System->Admin->Synaptic Package Manager and do a search for:

ntfs-3g

Install and the App will be in one of your drop down menus. Open it and it will ask which drives you would like to use.

If you format the drive as EXT3, it can definitely NOT be used on the common or garden Windows box. Would have no idea what the hell it was. So unless all the computers you intend to use this external drive on are Linux or can understand EXT3, I wouldn't advise it. :)

For future reference, just about any external drive, if you plug it in and switch it on, will be recognised by Ubuntu. Your ntfs format would have been recognised immediately and with 9.04, nfts-3g or something like it may already be included in the OS (I use 8.04 so don't know). Try first before going to such drastic measures! (unless of course you just had to have that drive EXT3 for some reason). 

[http://au.altavista.com/web/results?itag=ody&q=ntfs+ubuntu&kgs=0&kls=0](http://au.altavista.com/web/results?itag=ody&q=ntfs+ubuntu&kgs=0&kls=0)

Good luck with it all and good to hear all up and running.

:)

---

### Post by mikodo on 2009-06-23
> **Bucky Ball said:**
> Ubuntu reads/write to NTFS just fine. You could have left it as was. Go to System->Admin->Synaptic Package Manager and do a search for:

ntfs-3g

Install and the App will be in one of your drop down menus. Open it and it will ask which drives you would like to use.

If you format the drive as EXT3, it can definitely NOT be used on the common or garden Windows box. Would have no idea what the hell it was. So unless all the computers you intend to use this external drive on are Linux or can understand EXT3, I wouldn't advise it. :)

Thanks, I will. (Install ntfs-3g I mean).

Mikodo

---

### Post by Bucky Ball on 2009-06-23
I have edited my post #5 and added a link you might find useful. :)

---

### Post by mikodo on 2009-06-23
> **Bucky Ball said:**
> I have edited my post #5 and added a link you might find useful. :)

Wonderful post and thread! 

Suggestion:

Continue to make references to it in your posts. If you hadn't made the reference to it, I (and probably others) would have missed it, and would not have your advice handy for our next computer build.

Mike

---

### Post by Bucky Ball on 2009-06-23
Cheers and thanks Mikodo. Glad you liked it and hopefully find it some help. I will continue to reference as you suggest.

Good luck with your Ubuntu-ing and all things techno!

---

