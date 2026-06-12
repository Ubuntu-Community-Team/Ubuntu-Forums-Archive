---
title: "Capture mp4 stream"
date: 2010-08-05
forum: New to Ubuntu
---

### Post by Bob Bertrands on 2010-08-05
Hey

I need some help with saving video stream files to my computer.
From this site: [http://www.skynet.be/generation-nl/f.../Rock+Werchter]("http://www.skynet.be/generation-nl/festivals/vod/Rock+Werchter")  I can stream quite a few live show's (Supposedly you can only access  them if U use my ISP) and now I'd like to save some of them. I did this  before (as in last year) from the same site but back then they used  rtmp. Now they changed to this:

     ```
<script type="text/javascript"> 
          $j(function(){
              var manager_fv = {};
              manager_fv.lang = "nl";
              manager_fv.fest = 28;
              manager_fv.file = "mp4:werchter_2k10/concerts/balthazar_adsl.mp4";
              manager_fv.restricted = "true";
              manager_fv.concert = "true";
              manager_fv.bw =  "hi";
              manager_fv.vodPlayerUrl = "http://static.entertainment.portal.skynet.be/module/generationseg/swf/player5.1.swf";
              manager_fv.w = "486";
              manager_fv.h = "315";
              var manager_prms = {};
              manager_prms.allowscriptaccess = "always";
              var manager_attr = {};
              manager_attr.id = "vodManagerSwf";
              manager_attr.name = "vodManagerSwf";
              swfobject.embedSWF("http://static.entertainment.portal.skynet.be/module/generationseg/swf/festivals-vod-manager.swf?v=1280097733", "vodManager", "486", "315", "9", "http://static.www.portal.skynet.be/module/swf/expressInstall.swf", manager_fv, manager_prms, manager_attr);
          });
    </script> 
```On windows I  already tried a few of programs like replay media  catcher and flvcatcher but none of them seem to be able to catch this (I  did try them on other sites and there everything works fine).

As I have tried googling about everything I can think off and still have  no idea as to how to get these files, I'm getting pretty desperate so  someone please help me.

B


PS: I've posted the exact message before somewhere else but got no response.

---

### Post by target86 on 2010-08-13
Could be pretty easy since you downloaded the .flv files from last year... If you remember what the pre-URI was then just paste the filename here-after? (without the prefix mp4:). Alle the rest: the player, syntax, arguments are the same as last year...

Let me know if it worked...

---

