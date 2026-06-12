---
title: "Counter Strike sound issue"
date: 2011-04-26
forum: New to Ubuntu
---

### Post by jrs211 on 2011-04-26
hello... I was hoping for some help with a Counter Strike sound issue. I have spent the last couple of hours searching on the net for possible solutions but having little success. I am running Lucid and am trying to get CS to work. I have previously had it working fine but I think it was with Karmic. Right now when I 1st run CS it crashes almost immediately on the opening screen where the options/new game tabs etc are. After some reading it appears it has something to do with sound cofiguration in winecfg. I have tried with just ALSA selected - result is it crashes immediately. WIth OSS selected it doesn't crash but there is no sound. With EsounD selected there is sound but it is delayed. All very odd and I can't work out what to do...so I thought I'd ask for some help. Any would be appreciated.

---

### Post by calavier62 on 2011-04-26
WINE has known sound card issues. I would check [HTML]www.winehq.org[/HTML] for help, perhaps with the application's known issues.

---

### Post by marin123 on 2011-04-26
counter strike 1.6: dont change sound level while playing (or running cs)
if you dont have sound, close cs, run ```
pulseaudio -k
``` in terminal and start again...

leave winecfg on alsa...
at least that works for me..

maybe you could try reinstalling? what version of wine do you have?

---

### Post by jrs211 on 2011-04-27
thanks for your reply...

I just tried running CS after pulseaudio -k but again when in ALSA the game crashes on the opening screen. I'm running the latest version of Wine and I already tried a re-install of both although not sure if on deletion of Steam, CS and Wine all the files go completely if you see what I mean. My next step is maybe to try and rvert to an older version of Wine...worth a go I suppose. Thanks again.

---

