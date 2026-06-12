---
title: "Two SSH connections"
date: 2010-11-02
forum: New to Ubuntu
---

### Post by B34ST1Y on 2010-11-02
Hi,


Let's say I have Box1 & Box2. I ssh from my machine to Box1, then subsequently to Box2 from Box1. I did this from one terminal window. How do I communicate with Box1 WITHOUT killing the connection to Box2? 



Any help or insight would be greatly appreciated!

---

### Post by Hippytaff on 2010-11-02
Can you tunnell over https - [http://dag.wieers.com/howto/ssh-http-tunneling](http://dag.wieers.com/howto/ssh-http-tunneling)

---

### Post by marshmallow1304 on 2010-11-02
Open another terminal window and ssh to Box1 again.

OR

Once you've gotten to Box1, start a screen session
```
screen -S some-name ssh Box2
```
Now, you can press Ctrl+a followed by d to detach the screen and return to Box1 without terminating the connection to Box2.  To get back to the connection,
```
screen -dr some-name
```

---

### Post by B34ST1Y on 2010-11-02
Does anyone know if you can achieve this without a second connection to the machine? It doesn't scale well if you have to make a second one each and every time.

---

### Post by tom.swartz07 on 2010-11-02
Im not quite sure of the result that youre trying to get.

If you have 1 terminal window open on your computer and run 'screen', you could open 2 extra panes, allowing you to ssh to Box1 and Box2 at the same time. 

See the attached screenshot for an example of how that would look.


Is that what youre trying to get?
I use byobu and dvtm- theyre a lot more user friendly.

---

### Post by B34ST1Y on 2010-11-02
Ultimately yes that's what I want, but let's assume I can put whatever I want on my personal machine, but Box1 and Box2 are extremely stripped down machines that don't have any fancy programs installed. Basic bash. 


For the sake of the thread, can we also assume I can only connect to the machine on one instance? I want to tunnel traffic through Box2, but need to be able to interact with Box1 also.

---

### Post by B34ST1Y on 2010-11-03
Does anyone have any other suggestions? It HAS to be possible...




 *bump*

---

### Post by Boondoklife on 2010-11-03
I really don't think you are going to be able to do what you want as you can only have 1 connection open at a time on any given terminal. To do this you would have to be able to pass back information to the first box which you really just have a tunnel through.

Honestly I think screen is the only real option close to what you want.

---

