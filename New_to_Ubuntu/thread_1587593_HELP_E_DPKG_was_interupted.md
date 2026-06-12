---
title: "HELP E: DPKG was interupted"
date: 2010-10-03
forum: New to Ubuntu
---

### Post by DayLite on 2010-10-03
Help, I am in Nevada on the phone with a person in Ga. trying to help him with his problem. I too am very new and don't understand this.

I was explaining to him to type in the terminal:

> sudo add-apt-repository ppa:anonbeat/guayadeque sudo apt-get update sudo apt-get install guayadeque[FONT=Verdana][/FONT]

Yesterday he tried to install it using the [deb package]("http://sourceforge.net/projects/guayadeque/files/guayadeque/0.2.7/guayadeque_0.2.7%7Elucid-1_i386.deb/download"), When the actions appeared to stop installing he aborted it.

I tried today to do it by using the terminal, after putting in the above information, this came up:
> E: dpkg was interrupted. You must mannually run sudo dpkg-- configure -A/ to correct the problem.

Excuse any spelling errors as I just heard what he saw in the terminal.

HELP:confused:

---

### Post by jtarin on 2010-10-03
Run the command followed by the name of the application.
```
sudo dpkg-- configure -A/ <name of application>
```

That's your command not mine, but this is standard way to run a dpkg command followed by name of application. The command should be exactly as he reads it followed by a space then the app name.

---

### Post by andrewthomas on 2010-10-03
> **DayLite said:**
> Help, I am in Nevada on the phone with a person in Ga. trying to help him with his problem. I too am very new and don't understand this.
 
I was explaining to him to type in the terminal:
 
 
 
Yesterday he tried to install it using the [deb package]("http://sourceforge.net/projects/guayadeque/files/guayadeque/0.2.7/guayadeque_0.2.7%7Elucid-1_i386.deb/download"), When the actions appeared to stop installing he aborted it.
 
I tried today to do it by using the terminal, after putting in the above information, this came up:
 
 
Excuse any spelling errors as I just heard what he saw in the terminal.
 
HELP:confused: as the error message stated, try
 ```
sudo dpkg --configure -a
```

---

### Post by DayLite on 2010-10-03
> <name of application>

What is the name of the application? What do I put in?

---

### Post by jtarin on 2010-10-03
> **DayLite said:**
> What is the name of the application? What do I put in?

> **DayLite said:**
> sudo apt-get install guayadeque
I'm gonna take a real wild guess here and say "guayadeque", but let me get on the phone with the guy and I'll ask him.....got his number?:popcorn:

---

### Post by DayLite on 2010-10-03
> **jtarin said:**
> I'm gonna take a real wild guess here and say "guayadeque", but let me get on the phone with the guy and I'll ask him.....got his number?:popcorn:
This is wonderful of you to speak to him, I will send you a private message with his phone number, NOW

---

### Post by jtarin on 2010-10-03
There's not gonna be a language barrier is there, cause things might go slow if I have to use google translate? Why doesn't he come online to the forum and ask these questions?

---

### Post by DayLite on 2010-10-03
> **jtarin said:**
> There's not gonna be a language barrier is there, cause things might go slow if I have to use google translate? Why doesn't he come online to the forum and ask these questions?

We speak English, do you? He is so new to understanding computers. I will have to teach him how to register etc and that in itself is a challenge. Talking to him on the phone you are better than me to explain things.  I am so new and get so confused. I am a visual and without seeing the problem it is hard to grasp.

Please call him now.

---

### Post by jtarin on 2010-10-03
> **DayLite said:**
> We speak English, do you? He is so new to understanding computers. I will have to teach him how to register etc and that in itself is a challenge. Talking to him on the phone you are better than me to explain things.  I am so new and get so confused. I am a visual and without seeing the problem it is hard to grasp.

Please call him now.Called and the line is busy or not a working number....called the operator and she said the number is similar to Hawkinsville, GA area rather than Eastman. Just read him my first post and I'm sure he can figure it out.

---

### Post by DayLite on 2010-10-04
> **jtarin said:**
> . Just read him my first post and I'm sure he can figure it out.
I helped him and it is solved! Thank you for your support and quick response.

We spent a lot of time but this is what I had him do:

sudo dpkg --configure -a
sudo apt-get -f install

---

