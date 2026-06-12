---
title: "strange problem burning an install disk"
date: 2011-05-08
forum: New to Ubuntu
---

### Post by GrouchyGaijin on 2011-05-08
Hi Everyone,

I'm using 10.10 and recently noticed a weird thing when burning .iso files to disk.

In the past I've successfully used:
```

wodim dev=/dev/scd0 -v -data /path/to/isofile/

```

Starting the other day that command still burns a DVD and doesn't give an error messages, but I'm not able to boot from the DVD.

I can put the DVD in the drive and see it in Ubuntu.  I can open it up and see the files on it, but I can't boot from it.

I thought maybe the problem might be the media but that seemed unlikely since the blank DVDs are TDK 16x DVD-Rs. I figured TDK is a good brand and Japanese stuff is usually high quality.
(But for all I know they could have been made elsewhere and had a Japanese label slapped on them.)

Now the strange thing is when I tried to burn the exact same file to a DVD from the same pack of blanks, this time using the gui and following the instructions in the [Ubuntu Burning an ISO How To]("https://help.ubuntu.com/community/BurningIsoHowto") page.

That is:
Browse to the downloaded ISO image in the file browser.
Right click on the ISO image file and choose Write to Disc.

I was able to burn a bootable DVD.

Does anyone know why this would be the case?  I just don't know why the command line option would stop working all of a sudden.

---

