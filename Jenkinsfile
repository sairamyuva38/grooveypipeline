def gv

  pipeline{
    agent any
    parameters{
        choice(name:'VERSION',choices:['1.0.1','1.3.4','1.6.7'],description:'')
        booleanParam(name:'executeTests',defaultValue:true,description:'')
    }
    stages{
        
        stage("init"){
            steps{
                script{
                    gv= load "script.groovy"
                }
            }
        }
        
        
        stage("built"){
            steps{
                script{
                    gv.buildApp()
                }
            }
        }
        
        stage("test"){
            when{
                expression{
                    params.executeTests
                }
            }
            steps{
                script{
                    gv.testApp()
                }
            }
        }
        
        
        stage("deploy"){
            steps{
                 script{
                    gv.deployApp()
                }
            }
        }
        
    }
    
}
