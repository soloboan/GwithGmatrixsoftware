## Compute G using PLINK v1.9  

Genomic relationships will be computed with Yang et al 2010 implemented in PLINK v1.9

After computing the G matrix, additonal R functions are available to plot out fimilial relationships (i.e. Full-sib and Half-sib relationships)  

The script for making these plt are ported from https://github.com/soloboan/Fullsib_relationships.  
Read that page for description of the function.

### This is how to run the script for computing G with PLINK and ploting out the relationships  

#### compute the G matrix with PLINK
            'source('Gwithplink_andplotFSHSrel.R')'    
        
        genofile='dat2015G'      #   ==> genotype file  
        genoformat='binary'     #   ==> either binary or pedmap  
        outname='selC2015'    #   ==> outname of the computed G matrix  

            'Gwithplink(genofile,genoformat,outname)'  

### Output 
            outname.grm   ==> Genomic relationship in asreml format (row-column-value format)
            outname.id    ==> ordiginal IDs and coded ID of the animals 
            


#### Plot HS relationships  (read https://github.com/soloboan/Fullsib_relationships for explanation)
        grm=paste(outname,'.grm',sep='')  
        genolinkped=paste(outname,'.id',sep='')  
        pedigree='pedigree.txt'  
        outname='G2015_HS'  

            'MH_HS <- exFHsibrel_GRM(grm,pedigree,genolinkped,typefam = 'HS',exclfamsize=1,outname)'  


#### Plot FS relationships  (read https://github.com/soloboan/Fullsib_relationships for explanation)
        grm=paste(outname,'.grm',sep='')  
        genolinkped=paste(outname,'.id',sep='')  
        pedigree='pedigree.txt'  
        outname='G2015_FS'  

            'MH_FS <- exFHsibrel_GRM(grm,pedigree,genolinkped,typefam='FS',exclfamsize=1,outname)'  



