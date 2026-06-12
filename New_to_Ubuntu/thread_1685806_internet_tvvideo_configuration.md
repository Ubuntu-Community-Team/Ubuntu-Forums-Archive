---
title: "internet tv/video configuration"
date: 2011-02-11
forum: New to Ubuntu
---

### Post by PhilRogers34 on 2011-02-11
ok the problem i am having is as soon as i try and watch things over the internet my pc sounds like it is going to explode, if i put things into full screen display then my pc sounds like it is running at 100% this gets really irritating as it means i can't hear the programmes i want to watch. can anyone tell me how to configure my pc so i can stream tv and videos and watch them in full screen from websites without my pc going into overdrive?  also i do not need to adjust the volume, just to eliminate that solution before anyone suggests it thanks and why wont my posts on this forum allow me to write in paragraphs, it just puts all the text in one big chunk!!!

---

### Post by sydbat on 2011-02-11
> **PhilRogers34 said:**
> ok the problem i am having is as soon as i try and watch things over the internet my pc sounds like it is going to explode, if i put things into full screen display then my pc sounds like it is running at 100% this gets really irritating as it means i can't hear the programmes i want to watch. can anyone tell me how to configure my pc so i can stream tv and videos and watch them in full screen from websites without my pc going into overdrive?  also i do not need to adjust the volume, just to eliminate that solution before anyone suggests it thanks and why wont my posts on this forum allow me to write in paragraphs, it just puts all the text in one big chunk!!!To write in paragraphs, hit the Enter key (at least twice).

Now to your problem - can you tell us more about your computer hardware?
Is it a laptop? Desktop?
What make / model?
If custom built, what is the processor, RAM, graphics card?
Have you installed all the [Restricted Extras]("https://help.ubuntu.com/community/RestrictedFormats") and [Medibuntu]("https://help.ubuntu.com/community/Medibuntu")?

More info will help us help you.

---

### Post by PhilRogers34 on 2011-02-11
I have the following set up Packard bell istart 1360 Asus2 m2ns-nvm/s motherboard Amd Athlon 64 2ghz( ithink, 2.5g ram 80g hard drive 500g seagate portable hd i recently added an nvidia 8400gs 256mb graphics acelerator because the motherboard graphics packed up  i have installed ubuntu onto the ext hard drive  I have tried adjusting the display properties system>preferences>appearance  and set the visual effects to extra but it makes no difference, i get the first minute or two fine and then the computer just starts getting louder and louder.  thanks

---

### Post by PhilRogers34 on 2011-02-11
tried hitting the enter key twice     still no paragraphs    thanks

---

### Post by sydbat on 2011-02-11
> **PhilRogers34 said:**
> I have the following set up Packard bell istart 1360 Asus2 m2ns-nvm/s motherboard Amd Athlon 64 2ghz( ithink, 2.5g ram 80g hard drive 500g seagate portable hd i recently added an nvidia 8400gs 256mb graphics acelerator **because the motherboard graphics packed up**  i have installed ubuntu onto the ext hard drive  I have tried adjusting the display properties system>preferences>appearance  and set the visual effects to extra but it makes no difference, i get the first minute or two fine and then the computer just starts getting louder and louder.  thanksThe highlighted part - I imagine that your motherboard is going to stop functioning completely soon. This is a sign of a major hardware failure, and could explain the loudness from your system. 

I suggest you back everything up and install Ubuntu on another computer.

---

### Post by aeiah on 2011-02-11
sydbat is right, its only a matter of time (although to be honest, it doesnt mean you'll lose data when your motherboard finally dies of course)

it sounds like you havent got the nvidia drivers loaded for your new graphics card, or that perhaps the fan control on your graphics card is a bit too sensitive. it shouldn't be overheating by playing video content.

make sure you have the nvidia drivers loaded, and find a way of seeing the temperature of the card normally, and under the strain of videos (you should be able to use nvidia-settings to do this)

---

### Post by PhilRogers34 on 2011-02-11
i have the nvidia drivers installed, but when i use them it makes my browsing really slow on some sites so i stuck with one recommended on the drivers menu.  are you sure my pc is going to die? i really don't need the hassle of replacing it all, i shall try and use the settings to find the card temp, but once i have  this can i actually change the temperature or will it be just a reading i am given?

---

### Post by PhilRogers34 on 2011-02-11
ok, my driver temp is showing 50c when the pc is idle, i just tried watching the same programme to get a reading for when i'm playing vids and it stayed at 50c and the system didn't go into overdrive either, so it looks like this is going to be an occasional problem not a constant one, any ideas please?

---

### Post by PhilRogers34 on 2011-02-14
ok the temp is staying the same when it does it's thing,  it's taking a long time to buffer, is there any way i speed  up the buffering process, would increasing the size of my swap partition make any difference?

---

