---
title: "Amarok 2.4 0 tracks found library scans to 99%"
date: 2011-05-02
forum: New to Ubuntu
---

### Post by gobbledigook11 on 2011-05-02
Hi All,

OK - so very new user, 3 weeks in. Am loving Ubuntu and the community. Was running 10.10 but have upgraded to 11.04 this week. 

I had serious problems with Amarok in 10.10 but thought I might wait until 11.04 and see if there wasn't a resolution in Unity. There wasn't and so I decided to ask the community. I know everybody in here hates itunes, but I am yet to find something as 'easy' in terms of lay out and smart playlists, autorun cds (no matter how they are burnt) etc. Amarok is the option apparently but still can't get it to work!

I am running Amarok 2.4.0 and I cannot get any tracks to be scanned in the Local collection- always says 0 tracks. I can view the file in Amarok and can play them from there but Local collection says 0. It does crash periodically but when I run from the terminal in --debug it doesn't! (sorry). The scan gets to 99% fails then starts again. 

Also I had to uninstall because in 10.10 Amarok would start spontaneously when I started other programs (can't remember which ones now and it hasn't happened since 11.04). I did clear out the old files when I deleted it with --purge to make sure some default settings weren't causing strife everytime. 

I have got a very large library 80gig ish and this might be the problem, but haven't had any probs with banshee guayadeque or jajuk. 

I did play around with the MYSQL database stuff and was worried my var might be full or something.. but felt out of my depth so thought I'd better ask. 

Thanks

---

### Post by gidonmiller on 2011-05-30
Hi,
I'm having a similar issue. upgraded to 11.04 and amaroks collection is always empty. I ran 
```
amarokcollectionscanner -r /hd/Music
```
and this ran for awhile and finished with rc 0. I didnt verify that all my songs are there (I have a large collection. about 30G) but it seems ok (at least some of my songs should appear and none do).
I then purged amarok and mysql from my system and reinstalled but this didnt help either.
any ideas?
thanks, Gidon

---

