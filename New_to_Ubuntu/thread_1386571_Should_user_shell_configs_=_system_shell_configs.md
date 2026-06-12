---
title: "Should user shell configs = system shell configs?"
date: 2010-01-20
forum: New to Ubuntu
---

### Post by watchpocket on 2010-01-20
In my limited time with Ubuntu (about 2 months) I've seen that the [FONT=Courier New]**sudo**[/FONT] command gets invoked a whole lot for all sorts of almost daily admin tasks.

But once I invoke [FONT=Courier New]**sudo**[/FONT], i am abruptly yanked out of my familiar customized user shell environment, and suddenly, with me operating now as admin or super-user, the interface is clunky and not what I'm used to, and my fingers will instinctively type aliases that, all of a sudden, don't work when I'm over here in [FONT=Courier New]**sudo**[/FONT]-land.

So I want to copy all or most of my user zsh config files ( ~/.zshenv and ~/.zshrc , basically ) to the system /etc/zshenv and /etc/zshrc (which are currently empty, or nearly so) so that user configuration and system configuration match, or mostly match.

My only question: Is there any reason not to do that? Seems like it would make life a lot easier, though I can see might have to be careful when setting up, as root, an environment machine-wide.

---

### Post by llamabr on 2010-01-20
it'll work just fine.  edit the /etc/zshenv to include settings you want all users to have.

I thought sudo had a flag to allow you to use your own path, but checking the man page, i guess not.  I know su does.

anyway, ya, go for it.

---

