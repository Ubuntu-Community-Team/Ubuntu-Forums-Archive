---
title: "ubuntu laptop seen as a mobile device"
date: 2011-08-22
forum: New to Ubuntu
---

### Post by christyyazzie on 2011-08-22
Hello, I have an ancient HP pavilion ze1250 that I turned over to ubuntu 11.04 as the sole operating system.  So far all has been great other than minor things that I may end up coming back here for help with....

But today I got hit with one that I can't find any other info on when I google it:  My grocery store web sites, i.e. Safeway, Smith's.... will not allow me to use the "just for you" part of their sites now.  On that page, you are allowed to load grocery coupons on to your store card; it worked fine when I was an XP user, but now, when I go to that page it tells me that "Just for you is not available for mobile devices" and redirects me to the home page of the store.

Why would an Ubuntu OS appear as a "mobile device", and is there any way to fix this, like with something like Wine?  I know that Wine is for programs/software installs, but I thought maybe there was a similar app or a command or something that could be used to make the net see my laptop as an actual laptop, not a "mobile device"

If this has been addressed, I am sorry for bothering everyone and could you please just point me in the right direction?

Thank you so much

---

### Post by sanderd17 on 2011-08-22
you can just change your "user agent" (make the website think you use ie on a Windows). I believe there's a firefox add-on for it.

---

### Post by Wim Sturkenboom on 2011-08-22
It might be your browser's user agent string. Can't tell you exactly how to change it; will be an option in the browser that you can try to find. You can also search for "browser user agent" with your favorite search engine.

If they designed it 'properly', it might not help and you IE. Don't know anything about that (wine? virtual machine? or [http://www.google.co.za/#hl=en&source=hp&q=ie4linux+ubuntu+11.04&oq=ie4linux&aq=1&aqi=g8&aql=&gs_sm=e&gs_upl=2939l8925l0l11688l34l14l0l2l2l2l2349l8757l4-1.1.1.1.2.1l7l0&bav=on.2,or.r_gc.r_pw.&fp=e88e323d5ba2a154&biw=1280&bih=607](http://www.google.co.za/#hl=en&source=hp&q=ie4linux+ubuntu+11.04&oq=ie4linux&aq=1&aqi=g8&aql=&gs_sm=e&gs_upl=2939l8925l0l11688l34l14l0l2l2l2l2349l8757l4-1.1.1.1.2.1l7l0&bav=on.2,or.r_gc.r_pw.&fp=e88e323d5ba2a154&biw=1280&bih=607) ?)

---

### Post by christyyazzie on 2011-08-22
Thanks, I'll put firefox back on and try that again-- I'm used to chrome so I put chromium on and took firefox off; maybe that was the problem all along (chromium may be seen differently than regular chrome?)

---

### Post by sanderd17 on 2011-08-22
> **christyyazzie said:**
> Thanks, I'll put firefox back on and try that again-- I'm used to chrome so I put chromium on and took firefox off; maybe that was the problem all along (chromium may be seen differently than regular chrome?)

you can change the UA on chrom(e/ium) too. Apperently, you can do it this way: [http://www.google.com/support/forum/p/Chrome/thread?tid=64e4e45037f55919&hl=en](http://www.google.com/support/forum/p/Chrome/thread?tid=64e4e45037f55919&hl=en)

Just change the C:/.... by /usr/bin/chrome (or where ever your chrome installation is)

If you don't know where chrome is installed, execute
```

which chrome

``` (assuming chrome is the command to start the browser).

---

