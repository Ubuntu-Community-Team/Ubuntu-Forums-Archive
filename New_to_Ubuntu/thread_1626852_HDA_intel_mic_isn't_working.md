---
title: "HDA intel mic isn't working"
date: 2010-11-20
forum: New to Ubuntu
---

### Post by darkeye123 on 2010-11-20
Hey guys,

So i've used linux for a bit, but I have never really had an issue with the microphone or sound drivers, so I'm in a little bit over my head. 

I have a laptop with a microphone in the webcam, but I am trying to a third party headset in the microphone jack, which isn't even being picked up by audacity/skype.

So I looked around a bit, and I found this page:
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)
[Found out the HDA Intel using alsamixer]

So I followed the directions and:
```
cat /proc/asound/card0/codec#* | grep Codec

Which gave me:
Codec: IDT 92HD75B3X5

```So I searched through the file for 92HD75B3X5, but I didn't find any exact matches. At this point I am unsure of what to do. My laptop has three has three jacks on the front, so I wasn't sure whether to just pick one based upon description. Since I haven't done this before, I'm not sure what to do.

If anyone could provide any guidance, that would be great. 

Thank you for your time.

EDIT: forgot to mention the laptop I am using - it is an HP Pavilion DV6-2174CA. I noticed that there was an entry for the dv series, but it said dv5. Not sure whether this is the right driver or not.

---

