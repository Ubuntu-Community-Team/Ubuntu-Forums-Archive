---
title: "CD/DVD not displaying or getting recognized when loaded"
date: 2011-03-02
forum: New to Ubuntu
---

### Post by seventhsamurai on 2011-03-02
Hi Guys

Im having a bit of a peculiar problem. So I just ran an update this morning, following which I restarted the machine.

Whenever I insert a DVD into the drive, usually, the icon would pop up on the desktop and the volume would get loaded.

It isn't happening anymore, no matter what DVD I insert. So I went to /media directory and I see the DVD there, so I'm able to open it. But it doesn't show all the files, and only for certain discs am I able to right click there and eject. If I eject pressing the button on the drive, the disc ejects, but in the /media directory, I still see it displayed, even after refreshing. At this point, when I load a new DVD into the drive, it doesn't update it in the /media folder, and still displays the previous DVD.

Please help. I am running Ubuntu 10.10 and it's been running flawlessly on my system so far for the last few months. Just from this morning that this issue has been harassing me.

Thanks.

---

### Post by seventhsamurai on 2011-03-02
By the way, I can confirm that my DVD drive is working fine. It isn't giving me any problems under windows7.

---

### Post by Perfect Storm on 2011-03-02
Have you made any changes to the system? Like using "Ubuntu Tweak"?

---

### Post by seventhsamurai on 2011-03-02
No I havent made any changes of that sort.

I just realized that it's happening when I insert just one particular DVD. Strange issue.

I went into disk utility, unmounted the volume, and then ejected from there. Then other DVDs work fine and its back to normal. But if I put in this particular disc, and eject from the drive, then it doesnt read others after that.

---

### Post by houseworkshy on 2011-03-02
I had something similar with flash drives quite a long time ago which turned out to be a mounting problem.  Don't know if that is what this is however "man mount" typed in the terminal could give you some ideas.  As it was an update it could have been some error there.  If so lots of similar posts would suggest that it was the update itself whilst a lack of them would suggest that maybe something fluttered online with your own connection.  Perhaps updateing manally would correct things "sudo apt-get update" then "sudo apt-get upgrade".  If going back to a previous kernal doesn't sort it out you may be looking at the beginings of a hardware failure, dvd and cd drives ( especially burners ) tend to be the first things to go.

I was typing while others posted so ...... not so valid.

When Tommy Cooper told the doctor that raising his arm hurt and asked if there was anything he could do about it the doctor said "Certainly.  Don't do it"

Which is obvious though the puzzle is the persistant effect afterwards.  I simply don't know but you are getting advice from people who know more than me.  It may be worth mentioning if the dodgy dvd is encrypted, as in libdvdcss, or perhaps not.  Good luck with it.

---

