---
title: "How to remove older kernel, or should I not remove it?"
date: 2009-03-30
forum: New to Ubuntu
---

### Post by eddski on 2009-03-30
So I updated my OS, now when grub boots, I have a choice of two different Kernels. I've had the update long enough to know everything works. How do I (or should I) remove the old kernel? I'm not how much room it takes up, or would it be a good idea tojust keep it. Any auggestions?

---

### Post by bhishan on 2009-03-30
You can remove it. Take a look at the link below.

[http://ubuntuforums.org/showthread.php?t=1054269](http://ubuntuforums.org/showthread.php?t=1054269)

---

### Post by supersonicdarky on 2009-03-30
Generally it's a good idea to keep 2 versions. Thats what I do anyway. Having an extra one installed is ~100mb of space, which usually is not a concern.

---

### Post by leonardo_neo on 2009-03-30
Watch this tutorial........

> [http://www.youtube.com/watch?v=i7G91hIFyQI&eurl=http%3A%2F%2Fvideo.google.com%2Fvideosearch%3Fq%3Dremove%2Bold%2Bkernels%2BUbuntu%26oe%3DUTF-8%26rls%3Dcom.ubuntu%3Aen-US%3Aunofficial&feature=player_embedded](http://www.youtube.com/watch?v=i7G91hIFyQI&eurl=http%3A%2F%2Fvideo.google.com%2Fvideosearch%3Fq%3Dremove%2Bold%2Bkernels%2BUbuntu%26oe%3DUTF-8%26rls%3Dcom.ubuntu%3Aen-US%3Aunofficial&feature=player_embedded)

As it is already said, it is good idea to keep the present one, and the next to the recent one. Rest all you can remove.

:)

---

### Post by kansasnoob on 2009-03-30
Unless you're pressed for disc space I wouldn't bother. If your GRUB menu is cluttered you could edit it using startupmanager which is in Synaptic and after installed will show up in System Administration.

Look here:

[http://www.psychocats.net/ubuntu/startupmanager](http://www.psychocats.net/ubuntu/startupmanager)

If you click on the Advanced tab you can select how many kernels to keep:

[ATTACH]108101[/ATTACH]

NOTE: Always be sure to temporarily change that number to 2 when there is a kernel update until you know the new kernel works OK.

Also if you run the command:

```
sudo apt-get -f install
```

You may be prompted to remove older unused kernels (and/or other stuff) using the "sudo" apt-get autoremove command. Whenever I get that prompt I use copy-n-paste to send myself an email of what I'm removing - just in case something breaks! Then I can go to email (using any means) and make note of what I removed so I can go back to terminal after running recovery mode and reinstall what I removed from terminal.

---

