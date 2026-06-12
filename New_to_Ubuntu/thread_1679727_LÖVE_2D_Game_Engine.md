---
title: "LÖVE 2D Game Engine"
date: 2011-02-01
forum: New to Ubuntu
---

### Post by freelancer1995 on 2011-02-01
I was wondering if anybody had any experience of [LÖVE]("http://love2d.org/") on Ubuntu?  I have added it from the Software Centre then download the demos from the Love homepage.  Unzipped, double click and blank black screen.  See attached for the particles.love demo.  When run from the terminal, I get the following; 

freelancer@ub02:~/Programming/Love/demos$ love particles.love
This is LOVE 0.5.0 (Salted Nuts).

INIT love.filesystem [PhysFS]
INIT love.graphics [OpenGL/DevIL/FreeType]
INIT love.audio [SDL_mixer]
INIT love.timer [SDL]
INIT love.mouse [SDL]
INIT love.keyboard [SDL]
INIT love.physics [Box2D]
INIT love.lib [LuaSocket] 
INIT love.joystick [SDL]
INIT love.system [Generic]

blank black screen then close it and I get;

QUIT love.system [Generic]
QUIT love.joystick [SDL]
QUIT love.lib [LuaSocket] 
QUIT love.physics [Box2D]
QUIT love.keyboard [SDL]
QUIT love.mouse [SDL]
QUIT love.timer [SDL]
QUIT love.audio [SDL_mixer]
QUIT love.graphics [OpenGL/DevIL/FreeType]
QUIT love.filesystem [PhysFS]

Thanks in advance :-)

Love's website; [http://love2d.org/](http://love2d.org/)

---

### Post by thelinx on 2011-02-01
The issue is that the version of LÖVE (0.5.0) available in the Ubuntu repositories is old.

[IMG]http://img204.imageshack.us/img204/466/oldv.png[/IMG]

(It's two years old. Thanks, Canonical!)


Due to API changes inbetween versions, those demos wont work with that old version.
You should download the latest version of LÖVE from the frontpage you linked yourself to. We have .deb packages!


Good luck!

---

### Post by bartbes on 2011-02-01
I'd like to mention there's a ppa (mine, actually): ppa:bartbes/love-stable

---

### Post by freelancer1995 on 2011-02-02
I'll give it go tonight, thanks for your help :)

---

