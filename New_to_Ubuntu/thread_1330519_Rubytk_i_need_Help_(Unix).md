---
title: "Ruby/tk i need Help (Unix)"
date: 2009-11-18
forum: New to Ubuntu
---

### Post by SOB4ever33 on 2009-11-18
I am a complete beginner when it comes to programming and i need some help.
I don't know very much computer language jargan so please layman terms as much as possible.
I began trying to learn to program about a year ago when I took my first programming class:
1st language => Python => understood
2nd language => Java => no understanding whatsoever
3rd language => Ruby/tk => currently trying to learn, some basics understood, but i don't understand how to use blocks and several other huge concepts.

OBJECTIVE: create a GUI that stores browsing history in the form of Host name, IP address, and whether nearby hosts exists (Boolean + count).  Also, the user should be able to search the storage place by either host name or IP address to organize results.  
I am currently using Unix KDevelopRuby and i am running the program via the command line (ruby gui.rb) and i so far have:

#-------------------program begin------------------------------------------------

     #!/usr/bin/env ruby
  require 'tk'
   
  class HistBox
  inst_section = {
                  
  list1 = ["All Categories","Host Name", "IP Address", "Nearby Hosts", "Other Data of Interest"]
  list2 = [10,20,30,40,50,60,70,80]
  list3 = [10,20,30,40,50,60,70,80]
  @var = TkVariable.new
  @list2 = list2
   
  root = TkRoot.new do
                  title "History"
  end
   
  # ---------------Frame----------------------
  entry_frame = TkFrame.new(root) do
                  pack 'side' => 'top'
  end
   
  #----------Entry and DropDownMenu--------------
  entry1 = TkEntry.new(entry_frame) do
                  pack 'side' => 'left'
  end
  dropMenu = TkOptionMenubutton.new(root,@var,*list3) do
                  pack 'side'=>'top'
  end
   
  #--------------Buttons----------------------------
  button1 = TkButton.new(root) do
                  text "Search"
                  pack 'fill'=>'both', 'side' => 'top'
  end
  button2 = TkButton.new(root) do
                  text "Exit"
                  pack 'fill'=>'both', 'side' =>'top'
  end
  label = TkLabel.new(root) do
                  text "Search results: "
                  pack 'side' => 'left'
  end
                  
  button1.command proc { 
                  result = entry1.value.to_i * dropMenu.value.to_i 
                label.text = "The result is: #{result}"
  }
  button2.command { exit }
  end # -------------end class---------------------
  HistBox.new
  Tk.mainloop


#----------------------------------------program end--------------------------------------


as of now the program simply adds the entered value in entry1 to the value selected from the dropdownmenu and displays the result below following the "search results:" label.


however, i am now stuck, i would like the program to be able to talk to the hosts visited by the user and store this info somewhere so that it can be searched by this gui by either all categories or a specified category (change pull down menu to reflect list1 ) .
Also, i would like to produce the results in some sort frame following the Search results label, and i think it would be helpful to display the results in treeView unless anyone can think of a better idea.
TreeView example:
                       ___________________________
(sorry for the awkward lines everywhere i couldn't figure out how to add white space in this text box "_______" = indent)

_Search results:___________________
|   + [www.google.com]("http://www.google.com") 
                       | + [www.yahoo.com]("http://www.yahoo.com") 
                       |  - [www.aol.com]("http://www.aol.com") 
|____- Host Name                      |
                       |              __________- AOL                         |
                       |____       - IP Address                      |
                       | _________             - 999.999.9.9              |
                       |____       -Other Args                       |
                       | _________              - info                         |
                       |___________________|
So, yeah i hope that gives you guys a pretty good idea of what i'm trying to do so hopefully you might be able to help me.  Any advice is very much appriciated as i continue to guess and check my work :-/.  thank you for your time.

---

