---
title: "Problems with &quot;fsck&quot;"
date: 2009-03-02
forum: New to Ubuntu
---

### Post by RedStarYellowSun on 2009-03-02
My system no longer follows the commands:

"sudo touch fsck"

and

"sudo touch forcefsck"

When I type them, Terminal still asks me for my password. Thus, I see that it still recognizes and acknowledges them. But, when I restart my laptop to Ubuntu, it just loads it as though I never issued the command.

Please assist. All useful words of advice will be greatly appreciated.

Take care,
RedStarYellowSun

PS: I apologize for not putting the command in "Code" mode. I cannot seem to press the "Code" button in the "Post New Thread" page... Well, come to think of it, none of the buttons can be pressed. That seems... odd.

---

### Post by Miljet on 2009-03-02
I'm not sure what you are trying to do.

When you type sudo "anything" and the terminal prompts for your password, it is only acknowledging the sudo command.

```
sudo touch fsdisk 
```

All this does is change the timestamp of the fsdisk command.

---

### Post by Xiong Chiamiov on 2009-03-02
What files are those that you are touching?  I assume that they're some magic files to force a fsck on reboot?

You don't need special buttons; just put things between the [noparse]```

```[/noparse] tags.

---

### Post by RedStarYellowSun on 2009-03-02
> **Miljet said:**
> I'm not sure what you are trying to do.

When you type sudo "anything" and the terminal prompts for your password, it is only acknowledging the sudo command.

```
sudo touch fsdisk 
```

All this does is change the timestamp of the fsdisk command.

Really?... That explains quite a lot. Thanks for straignening me out.

Take care,
RedStarYellowSun

---

### Post by Xiong Chiamiov on 2009-03-02
You'll most often see touch used to create blank files, as updating the timestamp on a file that doesn't exist creates it.

You should really get to know what commands do before using them.  If you can't figure it out from Google and the man pages, go ahead and ask here.

---

### Post by RedStarYellowSun on 2009-03-02
> **Xiong Chiamiov said:**
> What files are those that you are touching?  I assume that they're some magic files to force a fsck on reboot?

You don't need special buttons; just put things between the [noparse]```

```[/noparse] tags.

Thanks for the code info.

Take care,
RedStarYellowSun

---

### Post by RedStarYellowSun on 2009-03-02
I see that Ubuntu Forums is a better source than a Google search. I got those commands from Google.
So, what commands can I give to start "fsck"?

---

### Post by RedStarYellowSun on 2009-03-02
Oh, I found it.
Thanks anyway, you two. I learned something new today.

Take care,
RedStarYellowSun

---

