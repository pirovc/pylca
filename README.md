# pylca

Adaptation of the the lowest common ancestor (LCA) algorithm originally developed by D. Eppstein (https://www.ics.uci.edu/~eppstein/)

## Installation

	python setup.py install

## Usage

    #Example:
	parent = {'b':'a','c':'a','d':'a','e':'b','f':'b','g':'f','h':'g','i':'g'}
	lcas = {
	    ('a','b'):'a',
	    ('b','c'):'a',
	    ('c','d'):'a',
	    ('d','e'):'a',
	    ('e','f'):'b',
	    ('e','g'):'b',
	    ('e','h'):'b',
	    ('c','i'):'a',
	    ('a','i'):'a',
	    ('f','i'):'f',
	}

	from pylca.pylca import LCA
	L = LCA(parent) # RestrictedRangeMin
	for k,v in lcas.items():
	    print("LCA RestrictedRangeMin", k, L(*k))

	from pylca.pylca import LogLCA
	L = LogLCA(parent) # LogarithmicRangeMin
	for k,v in lcas.items():
	    print("LCA LogarithmicRangeMin", k, L(*k))

	from pylca.pylca import OfflineLCA
	L = OfflineLCA(parent, lcas.keys()) # OfflineLCA
	for (p,q),v in lcas.items():
	     print("LCA OfflineLCA", (p,q), L[p][q])

## TODO

"Some experimentation would be needed to determine how large a query range needs to be to make this faster than computing the min of the range directly, and how much input data is needed to make the linear space version pay off compared to the much simpler LogarithmicRangeMin that it uses as a subroutine."