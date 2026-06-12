---
title: "Media Player Problems"
date: 2009-05-22
forum: New to Ubuntu
---

### Post by dunbrokin on 2009-05-22
I am trying to play one of these 1-click concerts....but all I get is 

javascript: void (0)


I have java and javascript enabled on my browser....I have been told that these concerts can be played in Ubuntu using VLC...I have downloaded VLC...but still cannot get them to play.

[http://www.classicalarchives.com/](http://www.classicalarchives.com/)

---

### Post by Zzl1xndd on 2009-05-22
Do you have the Mozilla VLC plug-in installed?

---

### Post by dunbrokin on 2009-05-22
> **tweakedenigma said:**
> Do you have the Mozilla VLC plug-in installed?

No, as it says that it is only experimental and puts your system at risk....does it?

---

### Post by Zzl1xndd on 2009-05-22
If its playing in your browser you may need to install it for it to work properly. I have been using it and haven't had any issues with it so far.

---

### Post by dunbrokin on 2009-05-22
> **tweakedenigma said:**
> If its playing in your browser you may need to install it for it to work properly. I have been using it and haven't had any issues with it so far.


Ok, installed the add-on in Firefox....and restarted....still nothing happens when I click on any of the "play" buttons...and I still get the same java message.

---

### Post by Zzl1xndd on 2009-05-22
I'm not sure what the issue might be, Hopefully someone with more experience with this issue will come along.

Might be worth attempting to clear your Java Cache though just to see. The Java control panel is normally listed under System > Preferences.

---

### Post by dunbrokin on 2009-05-22
> **tweakedenigma said:**
> I'm not sure what the issue might be, Hopefully someone with more experience with this issue will come along.

Might be worth attempting to clear your Java Cache though just to see. The Java control panel is normally listed under System > Preferences.

OK, thanks for your help anyway...

---

### Post by benerivo on 2009-05-22
I think it's just a javascript link. It looks like the download is a file that a media player could use to stream content. Do you have any firefox addons such as noscript enabled?

Try pasting this in to your firefox location bar and see what happens...
[http://www.classicalarchives.com/m/JCjPw2sU0aUwRsJl91ixuvW37w84adzM35yIKRVhF6JQLJHHoZ6T0hieLPkB7tXRon_Rjoc2zfZTdIg1isUVa0PTsNNxJZ2jkFyLOLKkgVs/-3SfVoGdEOjI_TOAeQNICA/m.wax](http://www.classicalarchives.com/m/JCjPw2sU0aUwRsJl91ixuvW37w84adzM35yIKRVhF6JQLJHHoZ6T0hieLPkB7tXRon_Rjoc2zfZTdIg1isUVa0PTsNNxJZ2jkFyLOLKkgVs/-3SfVoGdEOjI_TOAeQNICA/m.wax)

It is a file that points a media player back to the website so that it streams audio on your pc.

---

### Post by dunbrokin on 2009-05-22
> **benerivo said:**
> 

Try pasting this in to your firefox location bar and see what happens...
[http://www.classicalarchives.com/m/JCjPw2sU0aUwRsJl91ixuvW37w84adzM35yIKRVhF6JQLJHHoZ6T0hieLPkB7tXRon_Rjoc2zfZTdIg1isUVa0PTsNNxJZ2jkFyLOLKkgVs/-3SfVoGdEOjI_TOAeQNICA/m.wax](http://www.classicalarchives.com/m/JCjPw2sU0aUwRsJl91ixuvW37w84adzM35yIKRVhF6JQLJHHoZ6T0hieLPkB7tXRon_Rjoc2zfZTdIg1isUVa0PTsNNxJZ2jkFyLOLKkgVs/-3SfVoGdEOjI_TOAeQNICA/m.wax)

.

It says access denied.....!!

---

### Post by dunbrokin on 2009-05-22
> **benerivo said:**
> I think it's just a javascript link. It looks like the download is a file that a media player could use to stream content. Do you have any firefox addons such as noscript enabled?



I have no-script enabled...but I have white listed [http://www.classicalarchives.com/](http://www.classicalarchives.com/)

---

### Post by benerivo on 2009-05-22
Don't worry about it. It looks like the long string of letters in the link i gave was just useable for me in my current broesing session (i'm also getting 'access denied' after i've closed my browser and gone back in again). Anyway, the setup they use involves downloading  file a .wax file see here [http://www.fileinfo.com/extension/wax](http://www.fileinfo.com/extension/wax) which is opened by a media player, either automatically through a plugin, or later when ithe file is opened. I'm not using firefox, so i couldn't say exactly what you should do to get the music to play.

---

### Post by benerivo on 2009-05-22
As a test, try opening vlc, going to main menu > media > open network, and pasting this in the address...

mms://stream.classicalarchives.com/m/5XRzbsw-jxO28VE91AUSWrW7XBRsEGfDouIh5uTQV-RZ5RJdeh81vpyW5tDeb8_JQpMNb_E1FmE_FRBj2nd4Vvpuli-jvle7Q5zeqIxuxfE/LazrUWdJ0Wlp_Q4lP70xyw/m.wma


This is no solution for you, but it is just a test that you are theoretically able to play their stream.

---

### Post by dunbrokin on 2009-05-22
> **benerivo said:**
> As a test, try opening vlc, going to main menu > media > open network, and pasting this in the address...

mms://stream.classicalarchives.com/m/5XRzbsw-jxO28VE91AUSWrW7XBRsEGfDouIh5uTQV-RZ5RJdeh81vpyW5tDeb8_JQpMNb_E1FmE_FRBj2nd4Vvpuli-jvle7Q5zeqIxuxfE/LazrUWdJ0Wlp_Q4lP70xyw/m.wma


This is no solution for you, but it is just a test that you are theoretically able to play their stream.

Yup, that worked....music coming through loud and clear...

---

### Post by benerivo on 2009-05-22
I think the problem is with the way firefox trys to handle this javascript link. For me, i use another browser that just automatically downloads a .wax file that i can open in a media player, that will then download the music as an audio stream. Just to confirm - you aren't running any extra firefox addons, and that all you get when you click the play link is that 'javascript: void (0) message'?

---

### Post by dunbrokin on 2009-05-22
> **benerivo said:**
>  Just to confirm - you aren't running any extra firefox addons, and that all you get when you click the play link is that 'javascript: void (0) message'?

SORTED - thank you for the pointer and your help.....I set the Wax File
to use vlc in edit > preferences > applications.

It takes a while for vlc to kick in...but it did work just now. Will keep you posted on whether it continues to work or not.

---

