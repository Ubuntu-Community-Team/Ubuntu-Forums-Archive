---
title: "NVIDIA vs ATI/AMD graphics on Ubuntu"
date: 2011-02-26
forum: New to Ubuntu
---

### Post by pi.boy.travis on 2011-02-26
Greetings Comrades! I am building an Ubuntu machine, and the person I'm building for is looking for something suited for gaming/graphics intensive applications. I've only ever used Intel graphics cards for their excellent open-source drivers, but I'm thinking it's either going to be NVIDIA or ATI/AMD for this machine. So. . . Which would you recommend? In your experience, which is better for Ubuntu? Driver quality? Future-proof?

Thanks!

---

### Post by cascade9 on 2011-02-26
Generally-

nVidia has better closer source drivers, but ATI/AMD is catching up. 

ATI/AMD has better open source drivers. IMO nouveau (nvidia) sucks bigtime now, hopefully it will get better. I doubt they will catch ATI/AMD anytime soon. 

ATI has better image quality...not that you'll see many people talking about image quality these days. 

As for 'future proof', ATI/AMD IMO. 

I'd still normally recommend nVidia over ATI/AMD for linux distros, but its a lot closer than it was just a few years ago. 

BTW- the easiest nVidia card with for ubuntu with good performance and good price/performance is the GTX460. Try to get a 1GB model, not a 768MB model or a 460'SE' ('Slower Edition' LOL)

---

### Post by pi.boy.travis on 2011-02-26
> **cascade9 said:**
> Generally-

nVidia has better closer source drivers, but ATI/AMD is catching up. 

ATI/AMD has better open source drivers. IMO nouveau (nvidia) sucks bigtime now, hopefully it will get better. I doubt they will catch ATI/AMD anytime soon. 

ATI has better image quality...not that you'll see many people talking about image quality these days. 

As for 'future proof', ATI/AMD IMO. 

I'd still normally recommend nVidia over ATI/AMD for linux distros, but its a lot closer than it was just a few years ago. 

BTW- the easiest nVidia card with for ubuntu with good performance and good price/performance is the GTX460. Try to get a 1GB model, not a 768MB model or a 460'SE' ('Slower Edition' LOL)

I've heard that nouveau isn't exactly "consumer-ready." I'd like to stick with open-source drivers, keeping the impending integration of Wayland in mind.

---

### Post by cascade9 on 2011-02-26
Gaming on open soruce drivers? Umm, not a great idea. The reason why people use the closed source drivers for gaming is that 3D is a huge amount faster. 

As for wayland, its a long way from being useable. Its something to keep in mind for the future in some ways, but I wouldnt let the ubuntu plan to move to wayland make you use open source drivers now....

---

### Post by Frogs Hair on 2011-02-26
I read that Nvidia won't provide driver support for Wayland . If this is true I will have to move on to a distribution allows me to use the hardware of choice , which is Nvidia.

I can only hope that an accelerated 3d open source driver is ready when Wayland is implemented . Many things I have read about Ubuntu have not come some examples include the Gnome Shell in 10.10 , RGBA Transparency in 10.04 , Shopping indicators on title bars , and the list goes on.

Future proof ? is exactly that , a question mark.

---

### Post by pi.boy.travis on 2011-02-26
Do the open-source drivers not support hardware acceleration at all, or is the implementation not ideal?

---

### Post by cascade9 on 2011-02-26
You can get galluim (3D) but its got problems, and performance sucks compared to the closed drivers- 

[http://www.phoronix.com/scan.php?page=article&item=nouveau_gallium3d_june10&num=1](http://www.phoronix.com/scan.php?page=article&item=nouveau_gallium3d_june10&num=1)

---

### Post by pi.boy.travis on 2011-02-26
Thinking about this one. . .

[http://www.newegg.com/Product/Product.aspx?Item=N82E16814121370](http://www.newegg.com/Product/Product.aspx?Item=N82E16814121370)

---

### Post by cascade9 on 2011-02-26
A 6870 is faster, if you are thinking of going AMD.

---

### Post by I8NY on 2011-02-27
I have had ATI driver problems with ubuntu.  I also have a older pc with a old nvidia card and i have never had a problem with the driver.  So i would go nvidia unless you want the eyefinity ati has.  But i just go with the best value.

---

### Post by emoguitarist06 on 2011-02-27
[http://www.ubuntugamer.com/2011/01/ubuntu-graphics-driver-overview/]("http://www.ubuntugamer.com/2011/01/ubuntu-graphics-driver-overview/")

**Nvidia**

Nvidia are obviously one of the big two in the GPU industry alongside AMD/ATI. I believe (from reading computer mags) that their top of the range cards are currently outperforming AMD’s. But then again only a few months back AMD were outperforming across the entire price range, and I believe AMD still maintain the lead among budget cards. Anyway, I’m not going to talk too much about hardware performance, only to say that Nvidia and AMD are well ahead of everyone else. So what about drivers?

Nvidia provide only closed source drivers, with the exception of a very basic open source 2D only driver which until recently was used as the built-in driver for various distros (now replaced by the Nouveau driver). The closed source driver performs very well, and is generally almost on par with the Windows equivalent. Nvidia release driver updates unbelievably frequently, sometimes a few updates per-month! They also provide fast video acceleration using their VDPAU acceleration API. This is the only acceleration API supported by Adobe’s recent Flash beta. So if fullscreen HD video is something you use a lot, an Nvidia card with their own drivers may be your best bet.

Unfortunately, there are some downsides to the closed source Nvidia driver, the main one being that Nvidia still (after a few years now) do not support the Xrandr protocol which is the protocol that allows X to resize your screen resolution, or extend/clone to external monitors. This is why if you are running an Nvidia card, you can’t use Ubuntu’s built in screen resolution tool. This also causes problems with some apps that rely on Xrandr information for monitor positions. As Nvidia drivers tend to represent dual monitors to applications as one large one, sometimes a game might stretch across both rather than one (I know I’ve suffered this problem with Osmos). Another thing that Nvidia’s binary driver won’t support is kernel modesetting (KMS) and so no high-res Plymouth bootscreens – although the case is the same with most (all?) binary drivers.

On the open source side the Nouveau project have been developing 2D and 3D Nvidia drivers using reverse engineering for some time, and have made excellent progress. It’s likely now that in Natty if you have an Nvidia chip you may well get 3D acceleration straight off of a boot disk. Although performance in comparison with the closed driver is a lot worse, it’s normally good enough for simple games. One thing worth noting (if open source drivers are important to you) is that Nvidia have no intention of helping the Nouveau project with specifications, or answering questions and have made it quite clear that they are on their own.


**AMD/ATI**

Before AMD took over ATI, the track record of the ATI drivers was appalling. ATI drivers were notoriously buggy, and with no decent open source drivers ATI would always lose out to Nvidia if you were buying graphics hardware for Linux. That said, things are very different now.

Since AMD has taken over, the closed Linux drivers have come on in leaps and bounds. We now have regular monthly releases, and the drivers are rapidly becoming rock solid. My last big issue with the closed driver was fixed several months ago (slow minimizing/maximizing of windows when Compiz was running) and I have had no trouble since. Even better is that the closed AMD drivers support Xrandr so they integrate nicely with Ubuntu’s tools. Performance is excellent and now AMD cards tend to play nice with Wine, which never used to be the case. AMD also work with Canonical to get pre-release drivers out of the door ready for each Ubuntu release. Like the Nvidia driver, there is no KMS. The closed AMD drivers use a different video API to Nvidia called VA-API, unfortunately Adobe still hasn’t got around to supporting that, so Flash-based HD video does suffer a bit. Another drawback in comparison to Nvidia is that it takes some time for the closed AMD drivers to support new kernels and X server versions, but that shouldn’t be an issue if you use the default versions that come with an Ubuntu release.

On the open source front, AMD fair very well. Not only do AMD release card specifications to the open source community, but they also employ developers full time to work on the open source drivers. The drivers are currently undergoing a transition to the new Gallium3D framework, but that is almost complete and from now on we should start to see big improvements to the performance of these drivers. Basically, if you have an AMD card (that isn’t too recent a chipset – these things take time) you will get 3D acceleration out of the box on Ubuntu. Performance won’t be as good as the closed driver, but if that matters to you it’s just a click away. AMD really couldn’t do much more for Linux graphics driver development than they do, so kudos to them!


**Intel**

Intel are the open source kings of Linux graphics drivers. They only release open drivers for the platform. That means you get all the funky features like KMS, and Xrandr support. Their track-record isn’t entirely flawless though, if anyone owns a chipset based on the GMA500 you’ll know what I mean. Intel bought in a chipset from another company and rebranded it, only to find that they couldn’t develop open drivers for it. Cards with this chipset are almost unusable on a modern Ubuntu releases, apparently Intel are working on resolving that though.

The big drawback with Intel is their hardware performance is far lower than that of AMD and Nvidia, compound that with the fact that the open source driver stack has quite a lot of performance optimization to come and you may find that Intel just doesn’t cut it for games.


**Summary**

So, to sum up. If having open source driver support is important to you (e.g. it’ll work forever on Linux no matter what the release is), then Intel or AMD are the way to go. If performance matters (and you are on Ubuntu Gamer, so it probably does) your choices are Nvidia or AMD. In my opinion, AMD seems to just edge out because they support both the open source developers to produce a stable and compatible open driver, and also their users with a solid and fast closed driver, providing the best of both worlds.

---

### Post by BrownieBoy on 2011-04-19
@emoguitarist06

Great answer.  Thanks for that.

The URL that you quoted is a broken link though.  Ubuntugamer.com appears be omgubuntu.co.uk now.

---

