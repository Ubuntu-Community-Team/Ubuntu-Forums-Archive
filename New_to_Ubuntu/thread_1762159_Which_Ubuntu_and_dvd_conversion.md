---
title: "Which Ubuntu and dvd conversion"
date: 2011-05-18
forum: New to Ubuntu
---

### Post by Buck Buck on 2011-05-18
Hi All

I have recently gained an old pc, intel dual core 1.3Ghz and 1 Gb Ram.

I am converting all my dvd's to .avi and want to use this pc to do this. I would like to put Ubuntu on it, should I install Ubuntu 11 or an earlier release and also has anyone tried dvd conversion to avi using Ubuntu?

Cheers for any help given.

Buck Buck

---

### Post by Buck Buck on 2011-05-18
I should add that no removal of dvd encryption needs to be done with the dvd conversion to .avi

---

### Post by MartyBuntu on 2011-05-18
I use **AcidRip** for my DVD to .avi conversions.

Works perfectly.

---

### Post by Hedgehog1 on 2011-05-18
As to your OS choice, I think a 10.04.02 LTS install of Ubuntu is your safest and most reliable choice.

You want that system to be a stable workhorse.

***The Hedge***

:KS

---

### Post by rosencrantz on 2011-05-18
Considering it's not the fastest machine on earth and you'll need to conserve your ressources for DVD conversion, Xubuntu or Lubuntu might be worth a try. Those should also have long-term support with 10.04, I think.

---

### Post by Shibblet on 2011-05-18
> **Buck Buck said:**
> Hi All

I have recently gained an old pc, intel dual core 1.3Ghz and 1 Gb Ram.

I am converting all my dvd's to .avi and want to use this pc to do this. I would like to put Ubuntu on it, should I install Ubuntu 11 or an earlier release and also has anyone tried dvd conversion to avi using Ubuntu?

Cheers for any help given.

Buck Buck

Hey there Buckster.  I have been through this process over and over and over.  So, take it from a well seasoned video conversion veteran here.  AVI is not the way to go.  MKV is the best container format to use.

First and foremost, after your install of Ubuntu, you will want to install the Medibuntu ([www.medibuntu.org](www.medibuntu.org)) repository.  This gives you all of your needed codecs, and the ability to download some other files that will help with your DVD conversion.

So open up a terminal and type:  ```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```

This will add the repository and update your list.  Immediately following, type:  ```
sudo apt-get install libdvdcss2
```

This will allow for DVD Decryption, and removal of copy protection, without having to rp the DVD to your hard drive first.

Then you want to add one more repository, Handbrake.  This is hands down the best video encoding program available.  Your results will be spectacular, and the speed of the encode is unsurpassed.  Type:  ```
sudo add-apt-repository ppa:stebbins/handbrake-releases
```

Now that you've added Handbrake, download it by typing: ```
sudo apt-get install handbrake-gtk
```

Then insert a DVD to the drive, and run handbrake.

If you know anything about encoding, you should be good from there.  But trust me on the MKV file format.  If you are worried about compatibility on other systems, MKV is far more supported than AVI, and VLC Player will playback ANY type of video file.

---

### Post by mastablasta on 2011-05-19
> **Shibblet said:**
>  But trust me on the MKV file format. If you are worried about compatibility on other systems, MKV is far more supported than AVI, and VLC Player will playback ANY type of video file.
 
 
as long as the other system has a codec for it VLC will play it. so will other media players. 
 
but plenty people don't know about codecs, where to get them etc.

---

