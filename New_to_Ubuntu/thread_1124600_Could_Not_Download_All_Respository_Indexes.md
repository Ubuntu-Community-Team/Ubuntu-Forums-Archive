---
title: "Could Not Download All Respository Indexes"
date: 2009-04-13
forum: New to Ubuntu
---

### Post by Kensoi on 2009-04-13
Hi. Can Anyone Point Me In The Right Direction ?

Please See Attachment. Thanks. Ken

---

### Post by SunnyRabbiera on 2009-04-13
Hmm, might be a bad server or something...
This looks like the netbook remix, so I am unsure I can help you in full as I dont know much about it.

---

### Post by Copernicus1234 on 2009-04-13
I got it today at some point. Later it disappeared and now I dont get that message.

---

### Post by Kensoi on 2009-04-13
OK. Thanks For The Advice.

---

### Post by pspsampsp on 2009-04-13
have you added your any other repos than the ubuntu default ones? or made a typo when adding one cause i got that when i added the skype repository but spelt something wrong.

---

### Post by Kensoi on 2009-04-13
Not That I Can Remember.

---

### Post by pspsampsp on 2009-04-13
try changing to the main server if your not using it or to the server for your country if you are using the main server , go into system > administration > software sources and its under the tab ubuntu software.

---

### Post by Kensoi on 2009-04-13
Don't Seem To Have Software Sources. Sorry It's Under Admin Settings.

Ok Thanks. I'm Trying That Now.

---

### Post by Kensoi on 2009-04-13
I Changed The Settings. Still Receiving The Same Message.

---

### Post by llamabr on 2009-04-13
> **Kensoi said:**
> I Changed The Settings. Still Receiving The Same Message.

Well then, post the contents of your /etc/apt/sources.list

---

### Post by Kensoi on 2009-04-13
Hi. I'm Not Sure What That Means Or How To Do It. I'm New.

---

### Post by Kensoi on 2009-04-13
I'm Not Sure What That Means Or How To Do It. I'm Still Very Much A Newbie.

I Will Need To Go Soon So Any Advice Would Be Appreciated.

Thanks. Ken

---

### Post by Kensoi on 2009-04-13
I Am Now Able To Provide Sources List (/etc/apt)

---

### Post by Kensoi on 2009-04-14
There Are Three Lines On The Source List That Need To Be Changed (OUT OF DATE)

I Have Tried Changing The Settings On The Sources List. New entries should look like this: 

deb [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) hardy main restricted
deb [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) hardy-security main restricted


It Will Not Allow Me. Can Anyone Tell Me The Easiest Way To Do This ?

I Am Being Told I'm Not The Owner & Can't Change The Permissions.

As I Said Before I Am New To Ubuntu & Find It Difficult The Way Some Of The Instructions Are Written & Would Welcome Someone To Point Me On How I Can Change These Permissions. 

I'm Finding Editing Sudoers File A Bit Confusing.


Thanks Ken.

---

### Post by unutbu on 2009-04-14
Kensoi, do not edit your sudoers file. You do not need to do that to solve this problem, and if you do it the wrong way, you will have to go through a somewhat arcane process to fix your system.

To edit /etc/apt/sources.list, open a terminal (Applications>Accessories>Terminal) and type
```

gksu gedit /etc/apt/sources.list
```

Make your changes. Save and exit gedit.

Then in the terminal, type
```

sudo apt-get update

```

---

### Post by Kensoi on 2009-04-15
Thank You. Much Appreciated & It Worked Fine.

It's All Very New To Me. Ken

---

