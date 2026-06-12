---
title: "[SOLVED] Find command - Not in alphabetical order"
date: 2008-12-13
forum: New to Ubuntu
---

### Post by transmition on 2008-12-13
When using the "find" command, I have noticed that it does not seem to give me results in some kind of order. I suppose this would not be a problem for most people, but I like to combine the find command with mpg123 in order to listen to music. However, if you are listening to an mp3 audiobook, or an album that does not flow well out of order, then you have an issue.

So, this is what happens. I type in
```
/home/mason/Music/Pink\ Floyd/ -name "*.mp3"
```

and rather then getting something along the lines of:
```

/home/mason/Music/Pink Floyd/The Wall [Disc 1]/1-02 The Thin Ice.mp3
/home/mason/Music/Pink Floyd/The Wall [Disc 1]/1-03 Another Brick In The Wall (Part 1).mp3
/home/mason/Music/Pink Floyd/The Wall [Disc 1]/1-05 Another Brick In The Wall (Part 2).mp3

```

I get everything out of order:
```

/home/mason/Music/Pink Floyd/The Wall [Disc 2]/2-03 Nobody Home.mp3
/home/mason/Music/Pink Floyd/The Wall [Disc 2]/2-07 The Show Must Go On.mp3
/home/mason/Music/Pink Floyd/The Wall [Disc 2]/2-09 Run Like Hell.mp3
/home/mason/Music/Pink Floyd/The Wall [Disc 2]/2-08 In The Flesh.mp3
/home/mason/Music/Pink Floyd/The Wall [Disc 2]/2-10 Waiting For The Worms.mp3
/home/mason/Music/Pink Floyd/The Wall [Disc 2]/2-02 Is There Anybody Out There_.mp3
/home/mason/Music/Pink Floyd/The Wall [Disc 2]/2-13 Outside The Wall.mp3
/home/mason/Music/Pink Floyd/The Wall [Disc 2]/2-01 Hey You.mp3
/home/mason/Music/Pink Floyd/The Wall [Disc 2]/2-04 Vera.mp3
/home/mason/Music/Pink Floyd/The Wall [Disc 2]/2-11 Stop.mp3
/home/mason/Music/Pink Floyd/The Wall [Disc 2]/2-05 Bring The Boys Back Home.mp3
/home/mason/Music/Pink Floyd/The Wall [Disc 2]/2-06 Comfortably Numb.mp3
/home/mason/Music/Pink Floyd/The Wall [Disc 2]/2-12 The Trial.mp3
/home/mason/Music/Pink Floyd/Dark Side Of The Moon/11 My Friend Of Misery.mp3
/home/mason/Music/Pink Floyd/Dark Side Of The Moon/02 On The Run.mp3
/home/mason/Music/Pink Floyd/Dark Side Of The Moon/07 Any Colour You Like.mp3
/home/mason/Music/Pink Floyd/Dark Side Of The Moon/08 Brain Damage.mp3
/home/mason/Music/Pink Floyd/Dark Side Of The Moon/04 The Great Gig In The Sky.mp3
/home/mason/Music/Pink Floyd/Dark Side Of The Moon/06 Us And Them.mp3
/home/mason/Music/Pink Floyd/Dark Side Of The Moon/05 Money.mp3
/home/mason/Music/Pink Floyd/Dark Side Of The Moon/03 Time.mp3
/home/mason/Music/Pink Floyd/Dark Side Of The Moon/01 Speak To Me_Breathe.mp3
/home/mason/Music/Pink Floyd/Dark Side Of The Moon/09 Eclipse.mp3
/home/mason/Music/Pink Floyd/The Wall [Disc 1]/1-03 Another Brick In The Wall (Part 1).mp3
/home/mason/Music/Pink Floyd/The Wall [Disc 1]/1-09 Young Lust.mp3
/home/mason/Music/Pink Floyd/The Wall [Disc 1]/1-10 One Of My Turns.mp3
/home/mason/Music/Pink Floyd/The Wall [Disc 1]/1-08 Empty Spaces.mp3
/home/mason/Music/Pink Floyd/The Wall [Disc 1]/1-07 Goodbye Blue Sky.mp3
/home/mason/Music/Pink Floyd/The Wall [Disc 1]/1-13 Goodbye Cruel World.mp3
/home/mason/Music/Pink Floyd/The Wall [Disc 1]/1-02 The Thin Ice.mp3
/home/mason/Music/Pink Floyd/The Wall [Disc 1]/1-04 The Happiest Days Of Our Lives.mp3
/home/mason/Music/Pink Floyd/The Wall [Disc 1]/1-12 Another Brick In The Wall (Part 3).mp3
/home/mason/Music/Pink Floyd/The Wall [Disc 1]/1-06 Mother.mp3
/home/mason/Music/Pink Floyd/The Wall [Disc 1]/1-11 Don't Leave Me Now.mp3
/home/mason/Music/Pink Floyd/The Wall [Disc 1]/1-05 Another Brick In The Wall (Part 2).mp3

```

Could someone please inform me as to how I could make my search go in alphabetical order? Or at the very least, tell me if it is possible?
Thank you for any responses.

---

### Post by tuxxy on 2008-12-13
```
find ${ARGS} | sort
```

---

