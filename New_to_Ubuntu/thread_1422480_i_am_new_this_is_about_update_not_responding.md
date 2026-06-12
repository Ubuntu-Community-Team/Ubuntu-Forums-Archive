---
title: "i am new this is about update not responding"
date: 2010-03-05
forum: New to Ubuntu
---

### Post by sham1313 on 2010-03-05
after i sent this i saw this and dont know what icon i am suppose to click
Please click one of the Quick Reply icons in the posts above to activate Quick Reply.




1st let me say hi to everyone and let you know alto i have done computer sense 95 i am not a very good at computers. i sent this old laptop to my nephew and he fixed it for me with this new os in it. i am a very bad speller, i wish you had a spelling checker. i am also not very book smart. {SMILE}

I have only used windows from windows 95 up to proff. 2000. I just regester and this site said I had a pvt message and I click so it could be open in a different pages and it said a popup blocker wont let it do that. not sure what to do about that. 

how ever that was not the 1st thing I wanted to ask you about how to see that pvt message, that can be the second one, 

the 1st thing I need to ask you. what I need to know is the answer to this

I have a 2002 IBM laptop and the update is not reponding. I 1st ask the avast forum about what to do and they sent me here. on the new computer i use to use all I had to do was click ctrol alt delete and it would bring up task manger and i could close it that way. before bed yesterday i closed every thing but not te update because it was not respnding. how do i fix this. thanks Sharon

---

### Post by sham1313 on 2010-03-05
> **sham1313 said:**
> after i sent this i saw this and dont know what icon i am suppose to click
Please click one of the Quick Reply icons in the posts above to activate Quick Reply.




1st let me say hi to everyone and let you know alto i have done computer sense 95 i am not a very good at computers. i sent this old laptop to my nephew and he fixed it for me with this new os in it. i am a very bad speller, i wish you had a spelling checker. i am also not very book smart. {SMILE}

I have only used windows from windows 95 up to proff. 2000. I just regester and this site said I had a pvt message and I click so it could be open in a different pages and it said a popup blocker wont let it do that. not sure what to do about that. 

how ever that was not the 1st thing I wanted to ask you about how to see that pvt message, that can be the second one, 

the 1st thing I need to ask you. what I need to know is the answer to this

I have a 2002 IBM laptop and the update is not reponding. I 1st ask the avast forum about what to do and they sent me here. on the new computer i use to use all I had to do was click ctrol alt delete and it would bring up task manger and i could close it that way. before bed yesterday i closed every thing but not te update because it was not respnding. how do i fix this. thanks Sharon
i am not sure what i am doing,

---

### Post by MelDJ on 2010-03-05
go to applications-accesories-terminal.
then type in ```
sudo pkill apt
```

---

### Post by J V on 2010-03-05
> **sham1313 said:**
> i wish you had a spelling checkerI do... have you set your languages correctly?

> it said a popup blocker wont let it do that. not sure what to do about that.The bar at the top should let you click it and "Allow popups for ubuntuforums.org"

> I have a 2002 IBM laptop and the update is not reponding.Please open up synaptic and press reload, that should clear it up a bit...

> I 1st ask the avast forum about what to do and they sent me here. on the new computer i use to use all I had to do was click ctrol alt delete and it would bring up task manger and i could close it that way. before bed yesterday i closed every thing but not te update because it was not respnding. how do i fix this. thanks SharonHit alt-F2 and type in xkill, your mouse will turn into an X, then just click on the program you want to quit (Although hitting the X button on the window should give you a message asking it too)

I went to shortcuts and added xkill as ctrl-alt-X, very nice for when you have problems...

Also, you won't need antivirus on linux... Heres a paste from my mini-guides I keep for these situations :)
> **Viruses**
Linux has no viruses, not that it's not a popular target, google, yahoo, and several other multi-million dollar targets run on linux.

If there ever was a serious Linux virus out there, to get it to actually work, you would need to:

[LIST]
[*]Log onto your email
[*]Open your email
[*] Download the attachment
[*]Find the attachment
[*]Right-click and go to properties
[*]Go to the permissions tab
[*]Check the box marked execution
[*]Run the application (It can now infect the files in the same directory as it is in)
[*]Input your password (It can now infect files over the entire system)
[/LIST]
  On windows, all you have to do is to log onto your email, windows does the rest automatically, which leaves you open to viruses.

If you are still worried you will actually do this whole list without wondering if its a virus, the Ubuntu wiki has a nice list of [currently known Linux viruses]("https://help.ubuntu.com/community/Linuxvirus"), and their trivial (sometimes whimsical) natures.

You might still however, want to scan for windows viruses, so you don't infect your friends/colleagues with files from your computer (Which is equally unlikely as you would have to deliberately copy it over to them)

For this purpose you should install "[ClamTK]("apt://clamtk")" (Click to install) which is an interface for "ClamAV", which can scan incoming and outgoing email, or in your case, specific files.

---

### Post by sham1313 on 2010-03-24
I am trying to read and understand, but I do not know what WUB stands for. can you explane
Sharon   sham1313

> **MelDJ said:**
> go to applications-accesories-terminal.
then type in ```
sudo pkill apt
```

---

### Post by 2hot6ft2 on 2010-03-24
> **sham1313 said:**
> I am trying to read and understand, but I do not know what WUB stands for. can you explane
Sharon   sham1313
If you mean
"Keep your important files in HOSTS when ubuntu is installed with WUBI"
That's MelDJ's signature and has nothing to do with your questions or his post. If it's below the line ____________ then it's their signature.
WUBI is installing ubuntu inside windows like you would install an application. Basically.

For something like windows task manager you can right click on the top panel and select Add to Panel, select System Monitor, then click on Add.
It will add a system monitor to the top panel you can click on it to open it.
You could also add Force Quit the same way and if an app stops responding you can click on it then on the app. to force it to close.

There is a spell checker in the reply section and if the word is underlined with red you can right click on it and it will give you options for which spelling to use which you can click on and it will change the words spelling.

And if you close Update Manager and
Open a terminal
Applications > Accessories > Terminal
and run
```
sudo apt-get update
```
type in your password when prompted and hit Enter it wont be displayed.

It may fix the problem with Update Manager.

---

### Post by sham1313 on 2010-03-24
this post has help a lot and I thank you!! I am going to print this post and keep it under the computer. I mostly try to keep the computer like it should and my husband does the printer. if he is to busy  to help me with the printer I will hand copy. because with certain things i have to read and reread a lot to retain the information. when i write some times i invert letter and numbers with out knowing it. now let see if i can fine the spelling. smile

> **2hot6ft2 said:**
> If you mean
"Keep your important files in HOSTS when ubuntu is installed with WUBI"
That's MelDJ's signature and has nothing to do with your questions or his post. If it's below the line ____________ then it's their signature.
WUBI is installing ubuntu inside windows like you would install an application. Basically.

thanks that help a lot. I can see now how you can say this OS is kind of like windows. thanks again

For something like windows task manager you can right click on the top panel and select Add to Panel, select System Monitor, then click on Add.
It will add a system monitor to the top panel you can click on it to open it.
You could also add Force Quit the same way and if an app stops responding you can click on it then on the app. to force it to close.

There is a spell checker in the reply section and if the word is underlined with red you can right click on it and it will give you options for which spelling to use which you can click on and it will change the words spelling.
I well look again but I don't see in my part of the post. Iknpw me and my sppelling is bad. I keep saying if I right click on a word that is underline I have a chance to change,
I do see some underline words now. I see if it correct ,my mistake.:)

And if you close Update Manager and
Open a terminal
Applications > Accessories > Terminal
and run
```
sudo apt-get update
```type in your password when prompted and hit Enter it wont be displayed.

It may fix the only problem with Update Manager.
that one time only the   program would not close
it has work ever sence

you can see because I left the mistake there for  you to see, when I right it gave the menu like you said and click the check spelling.  nothing at all happen.
 you can tell me why?
thanks Sharon

---

