---
title: "Shoes.app problem"
date: 2010-03-25
forum: New to Ubuntu
---

### Post by Kalator on 2010-03-25
Pretty new to ubuntu but I really enjoy it!

my problem is with the Shoes application (which is a GUI program that runs the ruby programming language).  I downloaded the program through Ubuntu Software Center and the ruby language package through terminal.  I have a school assignment that I am working on but ran into a problem with it.  I emailed the code to my classmate and she was able to run it through her windows program for shoes.

When I run the program I get this message:
(eval):20: [BUG] Segmentation fault
ruby 1.8.7 (2009-06-12 patchlevel 174) [x86_64-linux]

Aborted

here is my code:
Shoes.app do
  def drawboard
    fill white
    stroke black
    rect(100, 100, 100, 100, 4)
    fill white
    stroke black
    rect(200, 200, 100, 100, 4)
    fill white
    stroke black
    rect(200, 100, 100, 100, 4)
    fill white
    stroke black
    rect(100, 200, 100, 100, 4)
  end

  def shape x, y
    stroke blue
    fill blue
    circle = oval(100, 100, 50)
    circle.move x, y
  end

  stack do
    flow do
      drawboard
    end
  end

  flow do
    @edit = edit_line
    @go = button("click")
  end

  @go.click do
    flow do
      e = @edit.text().to_i
      case e
        when e = 0
        shape 100, 100
      end
    end
    flow do
      e = @edit.text().to_i
      case e
        when e = 1
        shape 100, 200
      end
    end
  flow do
      e = @edit.text().to_i
      case e
        when e = 2
        shape 200, 100
      end
    end 
  flow do
      e = @edit.text().to_i
      case e
        when e = 3
        shape 200, 200
      end
    end
  end
end

the code when I run it works initially, but is aborted once tried.  The point of the code is to draw a board with 4 squares and have the user input a number between 0-3 and place a circle in the corresponding box.  will work on the windows shoes but won't work on ubuntu.

---

### Post by r-senior on 2010-03-25
It could be related to this bug (in Ruby, rather than Shoes) ...

[https://bugs.launchpad.net/ubuntu/karmic/+source/ruby1.8/+bug/488115]("https://bugs.launchpad.net/ubuntu/karmic/+source/ruby1.8/+bug/488115")

Your problem is not fixed in these changes (check the version numbers they quote). I installed Shoes and tried your app and I get the same problem. The version of Shoes/Ruby installed from the Karmic repositories seems to be fundamentally broken ...

```
$ shoes -v
/usr/lib/shoes/ruby/lib/optparse.rb:879: /usr/lib/shoes/ruby/lib/optparse.rb:879:in `basename': can't convert false into String (TypeError)
	from /usr/lib/shoes/ruby/lib/optparse.rb:879:in `program_name'
	from /usr/lib/shoes/ruby/lib/optparse.rb:735
	from /usr/lib/shoes/ruby/lib/optparse.rb:1298:in `call'
	from /usr/lib/shoes/ruby/lib/optparse.rb:1298:in `parse_in_order'
	from /usr/lib/shoes/ruby/lib/optparse.rb:1254:in `catch'
	from /usr/lib/shoes/ruby/lib/optparse.rb:1254:in `parse_in_order'
	from /usr/lib/shoes/ruby/lib/optparse.rb:1248:in `order!'
	from /usr/lib/shoes/ruby/lib/optparse.rb:1339:in `permute!'
	from /usr/lib/shoes/ruby/lib/optparse.rb:1360:in `parse!'
	from /usr/lib/shoes/lib/shoes.rb:127:in `args!'
	from (eval):0
/usr/lib/shoes/ruby/lib/optparse.rb:879: [BUG] Segmentation fault
ruby 1.8.7 (2009-06-12 patchlevel 174) [i486-linux]

Aborted
```

I then realised that Shoes isn't the best choice for an application name if you want to Google it. ;) I found it in the end ...

[http://shoes.heroku.com/downloads]("http://shoes.heroku.com/downloads")

I downloaded the Linux version (shoes2.run) to my Desktop (right-click and save), then

$ cd ~/Desktop
$ chmod +x shoes2.run
$ ./shoes2.run

... and I got your app to work OK. You can uninstall the Ubuntu shoes package. Can't see it being much good to you.

Obviously if you are going to keep this thing around for long, put it somewhere sensible like $HOME/bin rather than on your desktop.

---

### Post by Kalator on 2010-03-30
Ok I tried that and it did work for me.  Thank You!!! This makes things much easier.

I was worried that I'd have to switch to windows! :(

---

