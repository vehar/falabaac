#  falab - free algorithm lab 
#  Copyright (C) 2012 luolongzhi  罗龙智 (Chengdu, China)
#
#  This program is free software: you can redistribute it and/or modify
#  it under the terms of the GNU General Public License as published by
#  the Free Software Foundation, either version 3 of the License, or
#  (at your option) any later version.
#
#  This program is distributed in the hope that it will be useful,
#  but WITHOUT ANY WARRANTY; without even the implied warranty of
#  MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#  GNU General Public License for more details.
#
#  You should have received a copy of the GNU General Public License
#  along with this program.  If not, see <http://www.gnu.org/licenses/>.
#
#
#  filename: Makefile
#  version : 2.1.0.229
#  time    : 2019/07/14
#  author  : luolongzhi ( falab2012@gmail.com luolongzhi@gmail.com )
#  code URL: https://github.com/Sound-Linux-More/falabaac
#
#  comment : this file is the simple template which will be used in falab,
#            it will be changed according to the project
#


include ../Makefile.include

SHAREFLAG   = -fPIC -shared
DESTINCLUDE = ../include

INCLUDEDIR = ./include

ifeq ($(ARCH),ARCH_ARM)
LDFLAGS += -lm -lpthread -lrt 
else
LDFLAGS += -lm -lpthread -lrt 
endif

TARGET1   =  $(PLIB).a
TARGET2   =  $(PLIB).so.$(VERSION_MAJOR)
CSRCFILES =  $(shell ls *.c)
COBJFILES =  $(patsubst %.c,%.o,$(CSRCFILES))

SRCFILES  =	 $(CSRCFILES) 
OBJFILES  =	 $(COBJFILES) 

CFLAGS    += -I.  -I$(INCLUDEDIR)


all: $(OBJFILES) 
	@rm $(TARGET1) -f 
	@rm $(TARGET2) -f 
	$(CC) $(CFLAGS) -c $(OBJFILES) 	 
	$(AR) $(ARFLAG) $(TARGET1) $(OBJFILES)
	cp $(TARGET1) ..
	$(CC) $(SHAREFLAG) -Wl,-soname,$(TARGET2) -o $(TARGET2) $(OBJFILES)
	cp $(TARGET2) ..
	cp fa_aacapi.h $(DESTINCLUDE)
	cp fa_inttypes.h $(DESTINCLUDE)

clean : 
	@rm *.o -f
	@rm *.out -f	
	@rm $(TARGET1) -f	
	@rm $(TARGET2) -f	

install :

