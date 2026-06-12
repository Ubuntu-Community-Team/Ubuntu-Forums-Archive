---
title: "DVI to TV"
date: 2010-03-22
forum: New to Ubuntu
---

### Post by bnhrobotics on 2010-03-22
I have an nvidia graphics card which I am using nvidia-settings for. I can display 1024x768 on the TV through dvi. I think I can also do 800x600 or something similar. The TV is also supposed to handle 1080i and 720p (which I dont think I have options for with nvidia-settings). If the refresh rate is 60 Hz and I reset to hardware defaults, the display shows up on the TV. The output works fine on a monitor and the tv works fine when not in DVI mode. I have no other DVI outputting device made for a TV DVI input to test with unfortunately.

Problem 1 (Biggest):
There is severe ghosting, or essentially a double image. Everything has a shadow of itself. 

Problem 2: 
I seem to be suffering a loss in color resolution, but this may be due to the double image in problem 1

Problem 3:
The edges of the screen go off of the tv.

Problem 4:
Cant get a higher resolution to appear than 1024x768.

Any help is appreciated. Thanks!

---

### Post by daimaru on 2010-04-02
I just hooked up my panasonic plasma using a dvi to hdmi cable. So first question would be are you using the hdmi input on your tv or is it component , pc, or the one with the three cables (red white yellow) ? 

You need to connect using hdmi if you want to get high resolutions. Says so in my tv manual at least. 

Problem 3: Yeah had that same problem . its called overscan (googled alot to find the right name) you can solve it by installing the 195 nvidia drivers(i got 195.36.03 installed) . then under nvidia-settings you have a new option. Mine is located at 
->GPU 0  DFP-0 (Panasonic-TV) 
- There you have a slider called Overscan Compensation. Just slide it around until you can see your whole desktop.

As for the other problems maybe they are related to the connection cable your using. Try getting a hdmi cable and one of the DVI-to HDMI adpter things. Mine was included with the TV. Then try again with hight resolution.

Hope this helps a bit.

---

### Post by bnhrobotics on 2010-04-02
Thanks for the reply. My TV does not have HDMI, only DVI. The computer provides DVI. The TV is very finicky about resolution and refresh rate. I think the issues I am having are problems with the TV more than anything.

Thanks for the suggestion about the overscan. I am sure that will come in handy whenever I get the rest of the problems sorted out =)

---

