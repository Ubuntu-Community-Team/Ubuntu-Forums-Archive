---
title: "nohup not working wwhen updating"
date: 2022-07-27
forum: Networking &amp; Wireless
---

### Post by buill on 2022-07-27
hi im trying to update in the background and want the process to continue after i close the terminal the command im running is

 nohup sudo apt update && sudo apt upgrade -y


but closing the terminal kills to update how to i get it to keep updating in the background after the terminal closes

thanks_buill

---

### Post by #&amp;thj^% on 2022-07-27
Would this work instead?
```
sudo apt update && sudo apt upgrade -y & disown

```
I'm not sure "nohup" is your best option here.

---

### Post by The Cog on 2022-07-27
I would install screen, and run the command in there. But you may be able to get away with running two commands in a subshell, like this:
sudo nohup (apt update && sudo apt upgrade -y)

---

### Post by #&amp;thj^% on 2022-07-27
@The Cog, will you check this one, it works on my end, just want a trusted user for this:
```
sudo nohup apt update && sudo apt upgrade -y  &

```
EDIT my results:
```
$ sudo nohup apt update && sudo apt upgrade -y  &
[1] 28843
me@me-Standard-PC-Q35-ICH9-2009:~$ nohup: ignoring input and appending output to 'nohup.out'
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
[1]+  Done                    sudo nohup apt update && sudo apt upgrade -y



```
For the suggested code IE:
```
$ sudo nohup (apt update && sudo apt upgrade -y) 
bash: syntax error near unexpected token `('

```

---

### Post by buill on 2022-07-31
thanks for replys

sudo apt update && sudo apt upgrade -y & disown

gives output   [1] 3130

and does not update

---

### Post by buill on 2022-07-31
sudo apt update && sudo apt upgrade -y & disown -r

gives output 1]   Stopped                 sudo apt update && sudo apt upgrade -y

but i want them to keep going

---

### Post by buill on 2022-07-31
nohup sudo apt update && sudo apt upgrade -y & disown works the problem is im using sudo which them requires password but i have disowned the proccess so cant input password if 
su
password
apt update && sudo apt upgrade -y & disown
it works :) thanks

---

### Post by buill on 2022-07-31
found what i think is the best way to do it is

[COLOR=#067d17]echo password | sudo -S apt update && sudo apt upgrade -y & disown[/COLOR]

---

### Post by #&amp;thj^% on 2022-07-31
> **buill said:**
> found what i think is the best way to do it is

[COLOR=#067d17]echo password | sudo -S apt update && sudo apt upgrade -y & disown[/COLOR]


Yep I felt this was the best route to go , I knew my 1st suggestion was ify but it will work just not the way you would have expected to IE:
```
sudo nohup apt update && sudo apt upgrade -y  &
```
Starts the process in the first session, then simply hitting Return/Enter will finish the command.
That's my basis for I'm not sure "nohup" was your best option in my first post.
Good work though...:)

---

