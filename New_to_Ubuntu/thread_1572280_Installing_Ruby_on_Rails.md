---
title: "Installing Ruby on Rails"
date: 2010-09-10
forum: New to Ubuntu
---

### Post by lokisapocalypse on 2010-09-10
Hi all, 

I'm trying to set up Ruby on Rails on my Ubuntu machine (10.04) but I cannot seem to get the latest version of RubyGems. 

I try the following:

```

$ sudo rake gems:install
Rails requires RubyGems >= 1.3.2 (you have 1.3.0). Please `gem update --system` and try again.

```

Okay, easy enough. (I removed a lot of the output but will add it back if I need to). 

```

$ sudo gem update --system
Updating RubyGems
Updating rubygems-update
Successfully installed rubygems-update-1.3.0
Gem::SourceIndex#search support for String patterns is deprecated
/usr/local/lib/site_ruby/1.8/rubygems/commands/update_command.rb:97:in `execute' is outdated
Updating RubyGems to 1.3.0
Installing RubyGems 1.3.0
...

RubyGems installed the following executables:
	/usr/bin/gem1.8

If `gem` was installed by a previous RubyGems installation, you may need
to remove it by hand.

```

That was easy, let's try again. 

```

$ sudo rake gems:install
Rails requires RubyGems >= 1.3.2 (you have 1.3.0). Please `gem update --system` and try again.

```

D'oh. 

What am I doing wrong here?

---

### Post by lokisapocalypse on 2010-09-11
Any thoughts on this on? I really need to get this up and running today if at all possible.

---

### Post by dtay on 2011-10-14
try this 
 
$ sudo apt-get install update
 
i had the same problem when installing rails and it was an issue on ubuntu's side because i wasn't totally updated

---

