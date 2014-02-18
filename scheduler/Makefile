scheduler.pdf: scheduler.dvi
	dvipdf scheduler

#diagrams = net-traditional-stack.eps net-channels.eps
#
#%.eps: %.odg
#	unoconv -f eps $^

scheduler.dvi: $(wildcard *.tex) scheduler.bbl #$(diagrams)
	@-cp scheduler.aux scheduler.aux.save
	@echo LATEX scheduler
	@latex scheduler
	@if ! cmp -s scheduler.aux scheduler.aux.save; \
	then \
		echo BIBTEX scheduler; bibtex scheduler; \
	        cp scheduler.aux scheduler.aux.save; \
		echo LATEX scheduler; latex scheduler; \
	fi
	@if ! cmp -s scheduler.aux scheduler.aux.save; \
	then \
		echo LATEX scheduler; latex scheduler; \
	fi

scheduler.bbl: scheduler.bib
	latex scheduler
	bibtex scheduler
	latex scheduler

clean:
	rm -f scheduler.pdf scheduler.dvi #$(diagrams)
