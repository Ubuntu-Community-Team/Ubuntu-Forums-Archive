---
title: "Noscript Program Issues"
date: 2009-05-05
forum: New to Ubuntu
---

### Post by faron45 on 2009-05-05
I've been doing a little experimenting,because lately,ever since installing Noscript & Adblock plus I've been  having some problems using the Songza site [http://songza.com/]("http://songza.com/")

 First,I went to the site & without logging in,attempted to play some music.No go.I mention that because I believe that before things started going haywire,I was indeed able to play songs without logging in.So,really,I'm pretty sure that that had nothing to do with the problem.


 Next,I tried disabling my Adblock Plus,just for the Songza site,because I had done a search on Google for "songza & adblock plus" & found that some people were having problems associated with this.Still,no go.

 I next looked at my Noscript program again.Now,after initial install of Noscript & attempting to use the Songza site,I noticed that there were indeed quite a few scripts that Songza was attempting to run.I was actually quite shocked by the amount ! I was so shocked,I said to my girlfriend,"wow ! you gotta come take a look at this ! [because,I was trying to kind of teach her how to use the Noscript program as well as myself at the time].I mention this because after trying to get the site to work after "allowing" so many different scripts to run for this site,I happened upon one entitled "Imeem".

 Now,I believe,that this particular script was the one that actually allowed the site to work.PROBLEM...the site is no longer working the next time I attempt to use it.I go back & look through my "whitelist".And,again,begin looking at Noscript.

 Now,because I like to screw around with things,I had recently set all of my Noscript settings back to "default".Which meant that "Imeem" was no longer allowed to run.NEXT PROBLEM..."Imeem" is no longer listed as a script that Songza runs ! Hmmmmmmmmmmmmm ??? 

 So,I begin attempting to search for the offending culprit [script].I allowed every single script to run except:Googleadservices.com,Google-analytics.com,fbcdn.net & doubleclick.net.The running scripts are:songza.com,facebook.com & quantserve.com.And,the only reason that *these* scripts are running,is because I clicked on "allow scripts globally".Now,everything works fine with the site.

 But,what's weird about all this,is the fact that the scripts that were allowed to run [by clicking on "allow globally"],are the same ones that I just mentioned above & I had *already* allowed all 3 of those scripts to run before with no luck.So,what gives ??

  Does anyone know what my problem is ??  I cannot allow these settings to remain as they are [for one,it scares me] just so I can listen to a bit of music once in awhile,ya know ? My pc runs soooooo much better with Noscript running that I have kind of become accustomed to it.Can anyone help ?

                  Thankfully,faron45
                   aka:GuitarFiend.:guitar: 

 Sorry for such a long post,folks.Just wanted to make sure things were explained clearly for all of you.

---

### Post by collinp on 2009-05-05
There is probably some differences between pages on Songza or whatever it is, as they are generated dynamically, if I am correct. NoScript is probably not the best thing to be running if you want to do something like this :). I dont run it, and I am fine.

Also, FYI, Imeem is a music site that I use, located [here](http://www.imeem.com/) if you care.

---

### Post by faron45 on 2009-05-05
Hellow...thnks for info.I am not fmiliar with Imeem but,from what I've seen,they seem to be associated with Songza in some sort of way.Eventuually,I will probably give them a try.Thanks again.

---

### Post by Didius Falco on 2009-05-05
The "allow Globally" setting does just that - it allows every script on the site to run.

The imeem script: Songza apparently has some kind of deal with imeem (listed in Google as:>   *imeem* is the world's largest social music service with millions of free streaming songs and videos. Make playlists to share with friends and **...**So I'd say the logical reason you saw that script one time but not the other is because that's a tracking script from imeem that runs whenever some content from there is played on Songza.

---

### Post by faron45 on 2009-05-05
Didius,I am sorry but,you are not correct.It does not allow every script on the site to run.I have checked this on 2 different sites.In fact,on the Songza site,there seems to be only 4 out of 7 total scripts running [with "allow globally" set].And,even on *this* site,there is only 1 out of 3 running.Hmmmmmmmmmm ??

By the way...love that name.Heh,heh."Didius Falco".HmmmmmmmmmmmWhere'd that come from ?

---

### Post by Didius Falco on 2009-05-05
I was going by info from the No Script site. Maybe you did it a different way - I just scanned the site. I was more interested in the imeem script...

I've been Didius Falco for about 12-13 years now. I have always had trouble picking names for forums and games, and I'd just finished reading the very first Marcus Didius Falco book, so I took the name because it was fresh in my mind.

Another advantage to it is that anyone trying to get info on me has to wade through ten million sites about the books/character. I likes me some privacy...

---

