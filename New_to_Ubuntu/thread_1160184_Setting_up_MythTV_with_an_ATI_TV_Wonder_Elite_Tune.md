---
title: "Setting up MythTV with an ATI TV Wonder Elite Tuner?"
date: 2009-05-15
forum: New to Ubuntu
---

### Post by Mortus Pryde on 2009-05-15
I am trying to set up MythTV with my TV Tuner card, though I am not sure how to determine is my card is working in Ubuntu, if it is simply lacking the driver, and if the latter what driver I need in Ubuntu and where to get it. I have tried googling though all the referances I could find are for versions of Ubuntu that are now unsupported, and they are otherwise confusing.

Any help is much appreciated. Thanks.

---

### Post by e_james on 2009-05-19
I like to look through the unanswered posts to see if there is any topic where I might be able to contribute, but I do make a point of waiting for several hours in case someone else offers a better answer. Once I add a reply the thread will no longer appear on the unanswered list. In this case I was really hoping that someone knowledgeable would reply because I have similar questions. 

I would like to transfer most of my computer activity form Windows to Linux but one of the biggest hurdles is my video capture project. I have several PCI and USB capture devices and so far none of them works well (if at all) with Linux while they are at least adequate with Windows. It is generally recommended that you buy hardware known to work with Linux and this seems to be most applicable to TV capture cards. Unfortunately for me, I need analog tuners and these seem to have almost disappeared from the UK market, especially those known to be compatible with linux.

Over the past couple of years I have experimented with linux TV capture on several occasions and posted some questions similar to your own. So far I have received few replies and none of those was a solution to my difficulties. It seems that TV capture with linux is a particularly difficult topic and experts are few if any.

I recently upgraded one of my PCs to 9.04 (Jaunty) and I wondered if there would be any provement in the TV capture situation so I plugged in an MSI VOX tuner unit. The PC in question is a netbook so USB is the only choice. The first question was - did I have the drivers? After some research which seemed to require compiling kernel modules I came to the realisation that the drivers may already be installed (em28xx and video4linux). The main problem seems to be getting the settings right and this leads to your question. How do I test my work? Years ago I came to the conclusion that there are 3 or 4 key components in a computer which must all be working correctly for the computer to do anything. If any one is faulty, nothing happens and it is not at all obvious where the fault lies. This seems to be the situation with TV capture. You need drivers, appropriate settings and a suitable application or nothing much happens. TVTime seems to be a popular testing application but it gives no clues when the hardware won't cooperate. I did try MythTV with a Haupauge Win TV PCI FM card and one of the attempts actually produced a picture but the overall result wasn't satisfactory. I think I was using 7.10 or 8.04 at the time. The installation instructions for MythTV don't quite cover all the necessary details and this may or may not be significant.

I am aware that writing this comment will bring your thread back to the top of the list. Perhaps a new reader will be able to offer some help. Let's add another incentive by mentioning another tuner card - my Avermedia TV Studio, in case anyone does a search for it. And then there's my AverTV Cardbus card. I had a certain amount of success with that one but I couldn't get the sound to work. It was the same with both Windows and Linux using the Toshiba Tecra S1. I think there's a hardware bug in the sound system. The card seems to use the Line-in channel and the laptop has no Line-in socket. Toshiba had no incentive to make sure the Line-in channel would work.

---

### Post by Mortus Pryde on 2009-05-19
Actually the S1's have a tendance the develope excentric issues if any of the 4? boards that make up the mainboard develope the slightest fault. They will generally seem to work, but things will stop working quite right and become borderline functional. My company had aproximately a 60% RMA rate on these machine a few months back.

---

