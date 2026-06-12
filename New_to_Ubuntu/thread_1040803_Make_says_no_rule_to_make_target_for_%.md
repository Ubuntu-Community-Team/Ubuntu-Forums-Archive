---
title: "Make says no rule to make target for %"
date: 2009-01-15
forum: New to Ubuntu
---

### Post by _me_ubu_ on 2009-01-15
##############################################################
CPPFILES = ./src/common.cpp
CPPFILES += ./src/diskfile.cpp
CPPFILES += ./src/display.cpp

CPPOBJ=$(CPPFILES:.cpp=.oo)

all: clean $(TARGET)

$(TARGET) : $(COBJ) $(CPPOBJ) $(MAKEFILE)
	@$(ECHO) Linking objects...
	$(LD) $(LDFLAGS) $(LDDEFINES) $(CPPOBJ) -o $(TARGET)
	@$(ECHO)
	@$(ECHO) Completed!

%.oo : %.cpp $(MAKEFILE) $(HDRFILES)
	@$(ECHO) Compiling $<
	$(CC) -c $(CPPFLAGS) $(INC) $(CDEFINES) $< -o $@
	@$(ECHO)

clean :
	@$(ECHO) Cleaning...
	$(RM) $(TARGET) $(CPPOBJ) $(COBJ)
##############################################################

The content of make file is as above.
When I issue make, I get the following error:
make: *** No rule to make target `src/common.oo', needed by `mytarget'.  Stop.

Can anyone help please?

---

### Post by andrew.46 on 2009-01-16
Hi,

Can I ask what software you are compiling?

  Andrew

---

### Post by _me_ubu_ on 2009-01-16
Thanks for responding :)

It a flash tool which will flash the linux imahe with uboot and uImage. on an embedded device.

---

