#
# upgrade Makefile
#

PERL    ?=  /usr/bin/perl
PREFIX  ?=  `cat ../.prefix`

all: db tasks
	@echo
	@echo "Done applying changes. Now you should:"
	@echo 
	@echo "  * Check the file upgrade/error.log and correct any errors before continuing"
	@echo "  * After making sure that errors have been corrected, you may:"
	@echo "  * 'make install'"
	@echo "  * Stop and start Apache"
	@echo 

db:
	@echo
	@echo "Upgrading schema and data..."
	$(PERL) pre_updatedb # Remove after 1.0
	$(PERL) updatedb 2>error.log 

tasks:
	@echo	
	@echo "Performing various upgrade tasks"
	$(PERL) upgrade-tasks $(PREFIX)

notnull:
	@echo
	@echo "Adding NOT NULL constraints"
	$(PERL) fix_not_null.pl
