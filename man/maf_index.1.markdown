maf_index(1) -- build and examine MAF indexes
=============================================

## SYNOPSIS

`maf_index` [-t] <var>maf</var> <var>index</var><br>
`maf_index` `-d`|`--dump` <var>index</var>

## DESCRIPTION

**maf_index** is part of the bioruby-maf library and creates
Kyoto Cabinet indexes for Multiple Alignment Format (MAF)
files. These indexes enable other MAF tools to selectively extract
alignment blocks of interest.

In its default mode, `maf_index` parses the <var>maf</var> file given as an
argument and creates an index in <var>index</var>. 

The index data is stored in binary form, so with the `--dump`
argument, `maf_index` can dump out the index data in human-readable
form for debugging.

## FILES

The <var>maf</var> input file must be a valid MAF file of any length.

The index created is a Kyoto Cabinet TreeDB (B+ tree) database;
<var>index</var> must have a `.kct` extension.

## OPTIONS

TODO

 * `-d`, `--dump`:
   Instead of creating an index, dump out the given <var>index</var> in
   human-readable form. Index records will appear like:
   
       0 [bin 1195] 80082334:80082368
         offset 16, length 1087
         text size: 54
         sequences in block: 10
         species vector: 00000000000003ff

 * `-t`, `--threaded`:
   Use a separate reader thread to do I/O in parallel with
   parsing. Only useful on JRuby.

 * `--time`:
   Print elapsed time for index creation. Mainly useful for measuring
   performance with different Ruby implementations, I/O subsystems,
   etc.
   
## EXAMPLES

Build an index on a MAF file:

    $ maf_index chr22.maf chr22.kct
    
Dump out an index:

    $ maf_index -d chr22.kct > /tmp/chr22.dump

## ENVIRONMENT

`maf_index` is a Ruby program and relies on ordinary Ruby environment
variables.

## BUGS

`maf_index` does not currently allow Kyoto Cabinet database parameters
to be set.

## COPYRIGHT

`maf_index` is copyright (C) 2012 Clayton Wheeler.

## SEE ALSO

ruby(1), kctreemgr(1)

 * <https://github.com/csw/bioruby-maf/>
 * <http://fallabs.com/kyotocabinet/>



[SYNOPSIS]: #SYNOPSIS "SYNOPSIS"
[DESCRIPTION]: #DESCRIPTION "DESCRIPTION"
[FILES]: #FILES "FILES"
[OPTIONS]: #OPTIONS "OPTIONS"
[EXAMPLES]: #EXAMPLES "EXAMPLES"
[ENVIRONMENT]: #ENVIRONMENT "ENVIRONMENT"
[BUGS]: #BUGS "BUGS"
[COPYRIGHT]: #COPYRIGHT "COPYRIGHT"
[SEE ALSO]: #SEE-ALSO "SEE ALSO"


[maf_index(1)]: maf_index.1.html
